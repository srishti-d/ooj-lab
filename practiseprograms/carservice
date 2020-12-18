class CarService {
public static void main(String args[]){
Car_Queue q= new Car_Queue();
new Car_Owner(q);
new Car_Mechanic(q);
System.out.println("Press Ctrl+C to stop.");
}}
class Car_Queue{
int n;
boolean valueSet = false;
synchronized int get(){
while(!valueSet)
try{
wait();
}
catch (InterruptedException e){
System.out.println("InterruptedException caught");
}
System.out.println("Service Provided:"+n);
valueSet = false;
notify();
return n;
}
synchronized void put(int n)
{
while(valueSet)
try{
wait();}
catch(InterruptedException e){
System.out.println("InterruptedException caught");
}
this.n=n;
valueSet = true;
System.out.println("Order placed:"+n);
notify();
}}
class Car_Mechanic implements Runnable {
Car_Queue q;
Car_Mechanic(Car_Queue q){
this.q=q;
new Thread(this,"Car_Mechanic").start();}
public void run(){
int i=0;
while(true){
q.put(i++);
}}}
class Car_Owner implements Runnable {
Car_Queue q;
Car_Owner(Car_Queue q){
this.q=q;
new Thread(this,"Car_Owner").start();}

public void run()
{
while(true){
q.get();
}}}
