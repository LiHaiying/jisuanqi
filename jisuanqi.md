import java.awt.BorderLayout; 
import java.awt.GridLayout; 
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener; 
import javax.swing.JButton;
import javax.swing.JFrame; 
import javax.swing.JPanel; 
import javax.swing.JTextField; 
  
public class jsq extends JFrame{ 
 //第一个数
  
 String firstNum=""; 
 //第二个数
  
 String secondNum=""; 
 //判断是否点击了 = - * / 
 boolean flag=true; 
 //操作标记
 String biaoji=""; 
 public jsq(){ 
  setDefaultCloseOperation(DISPOSE_ON_CLOSE); 
  final JTextField tf_num=new JTextField(); 
  add(tf_num,BorderLayout.NORTH); 
  JPanel p=new JPanel();  
p.setLayout(new GridLayout(4,4)); 
  String str="789/456*123-0.=+"; 
  for(int i=0;i<str.length();i++){ 
   char c=str.charAt(i); 
   JButton b=new JButton(c+""); 
   p.add(b);  
   b.addActionListener(new ActionListener(){ 
  
    public void actionPerformed(ActionEvent arg0) { 
     ////得到选中的按钮
  
     Object obj=arg0.getSource(); 
     ////强制转换成 
     
     JButton select_btn=(JButton) obj; 
     ////得到按钮上的信息
  
     String values=select_btn.getText(); 
     //////////////////判断是否为数字
  
     if("1234567890.".indexOf(values)>=0){ 
        
      if(flag){ 
         
       String oid=tf_num.getText(); 
       tf_num.setText(oid+values); 
       
      }else{ 
         
       tf_num.setText(values); 
       flag=true; 
      }      
}
 /////////////////判断按钮为+ - * /中一个
 
     if("+-*/".indexOf(values)>=0){ 
        
      firstNum=tf_num.getText(); 
      biaoji=values; 
      flag=false; 
     }  
     if(values.equals("=")){ 
        
      double sum=0;  
      secondNum=tf_num.getText(); 
        
      if(biaoji.equals("+")){ 
         
     sum=Double.parseDouble(firstNum)+Double.parseDouble(secondNum); 
        
      } 
        
      if(biaoji.equals("-")){ 
         
     sum=Double.parseDouble(firstNum)-Double.parseDouble(secondNum); 
        
      }  
      if(biaoji.equals("*")){ 
               
     sum=Double.parseDouble(firstNum)*Double.parseDouble(secondNum); 
      }
     if (biaoji.equals("/")){ 
         
    sum=Double.parseDouble(firstNum)/Double.parseDouble(secondNum); 
        
      }       
      tf_num.setText(sum+""); 
      flag=false; 
      
     } 
    } 
     
   }); 
    
  } 
  add(p);  
  setSize(200, 200); 
  setVisible(true);  } 
 public static void main(String[] args) { 
    
  new jsq();
 }
  }
