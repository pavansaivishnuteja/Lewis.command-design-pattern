public class Command {
  
  private String methodName;
  private Object[] params;
  private Object object;
  
  public Command(String methodName, Object[] params, Object object) {
    this.methodName = methodName;
    this.params = params;
    this.object = object;
  }
  
  public void execute() {
    try {
      Method method = object.getClass().getMethod(methodName, getParamTypes(params));
      method.invoke(object, params);
    } catch (Exception e) {
      e.printStackTrace();
    }
  }
  
  private Class[] getParamTypes(Object[] params) {
    Class[] paramTypes = new Class[params.length];
    for (int i = 0; i < params.length; i++) {
      paramTypes[i] = params[i].getClass();
    }
    return paramTypes;
  }
}