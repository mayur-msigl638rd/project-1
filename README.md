# project-1

package rough ;

class display
{
	public void wish (String name)
	{
		synchronized(this)
		{
			for(int i =0 ; i< 10 ; i++)
			{
				System.out.print("hello : ");
				
				try 
				{
					Thread.sleep(2000);
				}catch(InterruptedException e)
				{
					
				}
				
				System.out.println(name);
				
			}
		}
	}
}

class mythread extends Thread
{
	display d;
	String name;
	
	public mythread(display d , String name)
	{
		this.d = d;
		this.name = name;
		
	}
	
	public void run()
	{
		d.wish(name);
	}
}

class rough
{
	
public static void main (String args[])
{
	display d = new display();
	
	mythread t1 = new mythread(d , "mayur");
	mythread t2 = new mythread(d , "monty");
	
	t1.start();
	t2.start();
}

}
