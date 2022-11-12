public class Command {
 
   public static void main(String[] args) {
 
       //create receiver object
       Receiver receiver = new Receiver();
 
       //create command object
       Command command = new ConcreteCommand(receiver);
 
       //set command object in invoker
       Invoker invoker = new Invoker();
       invoker.setCommand(command);
 
       //execute command
       invoker.executeCommand();
   }
}
 
//receiver class
class Receiver {
   public void performAction(){
       System.out.println("perform action");
   }
}
 
//command interface
interface ICommand {
   void execute();
}
 
//concrete command class
class ConcreteCommand implements ICommand {
 
   //object of receiver
   private Receiver receiver;
 
   public ConcreteCommand(Receiver receiver) {
       this.receiver = receiver;
   }
 
   @Override
   public void execute() {
 
       //calling method of Receiver
       receiver.performAction();
   }
}
 
//invoker class
class Invoker {
 
   ICommand command;
 
   public void setCommand(ICommand command) {
       this.command = command;
   }
 
   public void executeCommand() {
       //calling execute method of command interface
       command.execute();
   }
}
