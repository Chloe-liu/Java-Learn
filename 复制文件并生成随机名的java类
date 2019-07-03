package zg.dzdx.demo;

import java.io.BufferedInputStream;
import java.io.BufferedOutputStream;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.math.BigInteger;

public class Test {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		//获取当前测试路径并检查其存在合理性
		String path =  getTestPathStr();
		checkAndMkDir(path);
		
		//获取1970年至现在时间的毫秒数 和 四位随机数
		String time = "" + System.currentTimeMillis();
		String r = "" + (int)(Math.random()*10000);
		//十进制->十六进制
		String str = toHexString(time, r);
		
		//copyTextFile(path,str);
		copyByteFile(path,str);  
	}
	public static String getTestPathStr(){
		File file = new File("");
		String path = file.getAbsolutePath();//绝对路径
		System.out.println("当前目录："+path);
		String testPath = path + File.separator + "photo" + File.separator + "goods";
		return testPath;
	}
	
	public static void checkAndMkDir(String path){
		File file = new File(path);
		if(file.exists()){
			System.out.println("目录存在，"+path);
		}else{
			if(file.mkdirs()){
				System.out.println("目录创建成功："+path);
			}else{
				System.out.println("目录创建失败："+path);
			}
		}
	}
	
	public static void copyTextFile(String path,String str){
		File fileSource = new File(path + File.separator + "Test.java");
		//结果文件，由四位随机数和时间毫秒数的十六进制命名，保证命名的唯一性
		File fileDest = new File(path + File.separator + str + ".java");
		BufferedReader bufr = null;
		BufferedWriter bufw = null;
		try{
			bufr = new BufferedReader(		//文件->流->缓存
					   new InputStreamReader(
							new FileInputStream(fileSource)));
			bufw = new BufferedWriter(
					   new OutputStreamWriter(
							new FileOutputStream(fileDest),"utf-8"));
			String line;
			while((line = bufr.readLine()) != null){
				bufw.append(line);
				bufw.newLine();			//行分隔符
				System.out.println(line);
			}
			bufw.flush();//从缓存提交到磁盘，刷新流
		}catch(Exception e){
			
		}finally{
			if(bufr != null){
				try{
					bufr.close();//关闭流并释放相关资源
				}catch(IOException e1){
					e1.printStackTrace();
				}
			}
			if(bufw != null){
				try{
					bufw.close();
				}catch(IOException e1){
					e1.printStackTrace();
				}
			}
		}
	}
	
	public static void copyByteFile(String path,String str) {
		File fileSource=new File(path+File.separator+"ba.jpg");
		File fileDest=new File(path+File.separator+ str + ".jpg");
		
		BufferedInputStream  bufr=null;
		BufferedOutputStream bufw=null;
		try{
			bufr = new BufferedInputStream(new FileInputStream(fileSource));
	        bufw = new BufferedOutputStream(new FileOutputStream(fileDest));
	        byte[] buf=new byte[1024*3];
			int length,sumlen=0;
	        while((length=bufr.read(buf)) >0){
				bufw.write(buf,0,length);
				sumlen+=length;
				System.out.println("读写:"+length+"/"+sumlen+"字节");				
			}
			bufw.flush();
		}catch(Exception e){
			
		}finally{
			if(bufr != null){
				try{
					bufr.close();
				}catch(IOException e1){
					e1.printStackTrace();
				}
			}
			if(bufw != null){
				try{
					bufw.close();
				}catch(IOException e1){
					e1.printStackTrace();
				}
			}
		}
	}
	
	public static String toHexString(String time,String r){//十进制转十六进制
		String str = r + time;
		BigInteger data = new BigInteger(str,10);
		return data.toString(16);
	}
}
