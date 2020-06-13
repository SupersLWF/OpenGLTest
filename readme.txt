	
	在vs上配置OpenGL
	
	1. 下载库：
		a. 基本上都会是在这个路径下，或者相似的路径下，可以下载到glut，这个笔记使用的是vs2019+glutdlls37beta，文件本体应该可以在备份硬盘里找到，如果找不到，就使用下面的链接吧：http://www.opengl.org/resources/libraries/glut/glutdlls37beta.zip
		
	2. 配置库
		a. glut.h放在\Microsoft Visual Studio\2019\Community\VC\Tools\MSVC\14.24.28314\include下，你可以在这个路径下自定义新的路径，比如../OpenGL/glut.h
		b. glut.lib&glut32.lib放在../MSVC/14.24.28314/lib/x86下
		c. glut.dll&glut32.dll放在../SysWOW64路径下
		
	3. 测试库
		a. 创建一个完全空白的项目。
		b. 将以下代码添加其中：
			#include <gl/glut.h>
			void Initial(void)
			{
			    glClearColor(1.0f, 1.0f, 1.0f, 1.0f);          //设置窗口背景色为白色
			    glMatrixMode(GL_PROJECTION);        //指定设定投影参数
			    gluOrtho2D(0.0, 200, 0.0, 150.0);            //设置投影参数
			}
			void myDisplay(void)
			{
			    glClear(GL_COLOR_BUFFER_BIT);        //用当前背景色填充窗口
			    glColor3f(0.0f, 0.0f, 0.0f);                  //设置当前的绘图颜色为黑色
			    glRectf(50.0f, 100.0f, 150.0f, 50.0f);          //绘制一个矩形
			    glFlush();                          //清空OpenGL命令缓冲区，执行OpenGL命令 
			}
			int main(int argc, char* argv[])
			{
			    glutInit(&argc, argv);
			    glutInitDisplayMode(GLUT_RGB | GLUT_SINGLE); //初始化窗口的显示模式
			    glutInitWindowPosition(100, 100);                //设置窗口的位置
			    glutInitWindowSize(400, 400);                   //设置窗口的大小
			    glutCreateWindow("第一个OpenGL程序");       //创建窗口
			    glutDisplayFunc(&myDisplay);                  //设置当前窗口的显示回调函数
			    Initial();                                     //完成窗口初始化
			    glutMainLoop();                              //启动主 GLUT事件处理循环
			    return 0;
			}
		c. 在project -> manage NuGet packages..下搜索 nupengl ,并安装第一项
		d. 点击调试，如果程序成功运行，则OpenGL在vs上便配置成功了。
			
