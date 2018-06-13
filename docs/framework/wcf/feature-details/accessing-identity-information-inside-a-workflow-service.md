---
title: Přístup k informacím o identitě v rámci služby pracovních postupů
ms.date: 03/30/2017
ms.assetid: 0b832127-b35b-468e-a45f-321381170cbc
ms.openlocfilehash: a87c21215c37fefd8d9306fd0ccd0c5b2a1dfd11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491972"
---
# <a name="accessing-identity-information-inside-a-workflow-service"></a><span data-ttu-id="e0f66-102">Přístup k informacím o identitě v rámci služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e0f66-102">Accessing Identity Information inside a Workflow Service</span></span>
<span data-ttu-id="e0f66-103">Chcete-li získat přístup k o identitě v rámci služby pracovních postupů, musíte implementovat <xref:System.ServiceModel.Activities.IReceiveMessageCallback> rozhraní pro provádění vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e0f66-103">To access identity information inside a workflow service, you must implement the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interface in a custom execution property.</span></span> <span data-ttu-id="e0f66-104">V <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> metoda dostanete <xref:System.ServiceModel.OperationContext.ServiceSecurityContext> přístup k informacím identity.</span><span class="sxs-lookup"><span data-stu-id="e0f66-104">In the <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> method you can access the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext> to access identity information.</span></span> <span data-ttu-id="e0f66-105">Toto téma vás provede procesem implementace tato vlastnost spouštění, jakož i vlastní aktivity, která bude surface této vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity za běhu.</span><span class="sxs-lookup"><span data-stu-id="e0f66-105">This topic will walk you through implementing this execution property, as well as a custom activity that will surface this property to the <xref:System.ServiceModel.Activities.Receive> activity at runtime.</span></span>  <span data-ttu-id="e0f66-106">Vlastní aktivity budou implementovat stejné chování jako <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` aktivity, s výjimkou, že pokud <xref:System.ServiceModel.Activities.Receive> je umístěn uvnitř, <xref:System.ServiceModel.Activities.IReceiveMessageCallback> bude volána a informace o identitě bude načten.</span><span class="sxs-lookup"><span data-stu-id="e0f66-106">The custom activity will implement the same behavior as a <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity, except that when a <xref:System.ServiceModel.Activities.Receive> is placed inside of it, the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> will be called and the identity information will be retrieved.</span></span>  
  
### <a name="implement-ireceivemessagecallback"></a><span data-ttu-id="e0f66-107">Implementace IReceiveMessageCallback</span><span class="sxs-lookup"><span data-stu-id="e0f66-107">Implement IReceiveMessageCallback</span></span>  
  
1.  <span data-ttu-id="e0f66-108">Vytvořte prázdnou [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] řešení.</span><span class="sxs-lookup"><span data-stu-id="e0f66-108">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution.</span></span>  
  
2.  <span data-ttu-id="e0f66-109">Přidejte novou aplikaci konzoly s názvem `Service` k řešení.</span><span class="sxs-lookup"><span data-stu-id="e0f66-109">Add a new console application called `Service` to the solution.</span></span>  
  
3.  <span data-ttu-id="e0f66-110">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="e0f66-110">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="e0f66-111">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="e0f66-111">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="e0f66-112">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e0f66-112">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="e0f66-113">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="e0f66-113">System.ServiceModel.Activities</span></span>  
  
4.  <span data-ttu-id="e0f66-114">Přidejte novou třídu s názvem `AccessIdentityCallback` a implementovat <xref:System.ServiceModel.Activities.IReceiveMessageCallback> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e0f66-114">Add a new class called `AccessIdentityCallback` and implement <xref:System.ServiceModel.Activities.IReceiveMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class AccessIdentityCallback : IReceiveMessageCallback  
    {  
       public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
       {  
          try  
          {  
             Console.WriteLine("Received a message from a workflow with the following identity");  
             Console.WriteLine("Windows Identity Name: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.Name);  
             Console.WriteLine("Windows Identity User: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.User);  
             Console.WriteLine("Windows Identity IsAuthenticated: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.IsAuthenticated);  
          }            
          catch (Exception ex)  
          {  
             Console.WriteLine("An exception occurred: " + ex.Message);  
          }  
        }  
    }  
    ```  
  
     <span data-ttu-id="e0f66-115">Tento kód používá <xref:System.ServiceModel.OperationContext> předán do metody informací o identitě přístup.</span><span class="sxs-lookup"><span data-stu-id="e0f66-115">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to access identity information.</span></span>  
  
### <a name="implement-a-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="e0f66-116">Implementace nativní aktivity pro přidání do NativeActivityContext IReceiveMessageCallback implementace</span><span class="sxs-lookup"><span data-stu-id="e0f66-116">Implement a Native activity to add the IReceiveMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="e0f66-117">Přidání nové třídy odvozené od <xref:System.Activities.NativeActivity> názvem `AccessIdentityScope`.</span><span class="sxs-lookup"><span data-stu-id="e0f66-117">Add a new class derived from <xref:System.Activities.NativeActivity> called `AccessIdentityScope`.</span></span>  
  
2.  <span data-ttu-id="e0f66-118">Přidejte ke sledování podřízené aktivity, proměnné, index aktuální aktivity, místní proměnné a <xref:System.Activities.CompletionCallback> zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e0f66-118">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="e0f66-119">Implementace konstruktoru</span><span class="sxs-lookup"><span data-stu-id="e0f66-119">Implement the constructor</span></span>  
  
    ```  
    public AccessIdentityScope() : base()  
    {  
        this.children = new Collection<Activity>();  
        this.variables = new Collection<Variable>();  
        this.currentIndex = new Variable<int>();  
    }  
    ```  
  
4.  <span data-ttu-id="e0f66-120">Implementace `Activities` a `Variables` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e0f66-120">Implement the `Activities` and `Variables` properties.</span></span>  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  <span data-ttu-id="e0f66-121">přepsání <xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="e0f66-121">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="e0f66-122">přepsání <xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="e0f66-122">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
    {  
       // Add the IReceiveMessageCallback implementation as an Execution property   
       context.Properties.Add("AccessIdentityCallback", new AccessIdentityCallback());  
       InternalExecute(context, null);  
    }  
  
    void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
    {  
       //grab the index of the current Activity  
       int currentActivityIndex = this.currentIndex.Get(context);  
       if (currentActivityIndex == Activities.Count)  
       {  
          //if the currentActivityIndex is equal to the count of MySequence's Activities  
          //MySequence is complete  
          return;  
       }  
  
       if (this.onChildComplete == null)  
       {  
          //on completion of the current child, have the runtime call back on this method  
          this.onChildComplete = new CompletionCallback(InternalExecute);  
       }  
  
       //grab the next Activity in MySequence.Activities and schedule it  
       Activity nextChild = Activities[currentActivityIndex];  
       context.ScheduleActivity(nextChild, this.onChildComplete);  
  
       //increment the currentIndex  
       this.currentIndex.Set(context, ++currentActivityIndex);  
    }  
    ```  
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="e0f66-123">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e0f66-123">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="e0f66-124">Otevřete existující `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="e0f66-124">Open the existing `Program` class.</span></span>  
  
2.  <span data-ttu-id="e0f66-125">Definujte následující konstanty:</span><span class="sxs-lookup"><span data-stu-id="e0f66-125">Define the following constants:</span></span>  
  
    ```  
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  <span data-ttu-id="e0f66-126">Přidat statickou metodu s názvem `GetWorkflowService` vytvářející služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e0f66-126">Add a static method called `GetWorkflowService` that creates the workflow service.</span></span>  
  
    ```  
    static Activity GetServiceWorkflow()  
    {  
       Variable<string> echoString = new Variable<string>();  
  
       // Create the Receive activity  
       Receive echoRequest = new Receive  
       {  
          CanCreateInstance = true,  
          ServiceContractName = contract,  
          OperationName = "Echo",  
          Content = new ReceiveParametersContent()  
          {  
             Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
          }  
       };  
  
       return new AccessIdentityScope  
       {  
          Variables = { echoString },  
          Activities =  
          {  
             echoRequest,  
             new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
             new SendReply  
             {  
                Request = echoRequest,  
                Content = new SendParametersContent()  
                {  
                   Parameters = { { "result", new InArgument<string>(echoString) } }   
                }  
             }  
          }  
       };  
     }  
    ```  
  
4.  <span data-ttu-id="e0f66-127">Ve stávající `Main` metoda hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e0f66-127">In the existing `Main` method, host the workflow service.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       string addr = "http://localhost:8080/Service";  
  
       using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
       {  
          WSHttpBinding binding = new WSHttpBinding(SecurityMode.Message);  
          host.AddServiceEndpoint(contract, binding, addr);  
  
          host.Open();  
          Console.WriteLine("Service waiting at: " + addr);  
          Console.WriteLine("Press [ENTER] to exit");  
          Console.ReadLine();  
          host.Close();  
       }  
    }  
    ```  
  
### <a name="implement-a-workflow-client"></a><span data-ttu-id="e0f66-128">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e0f66-128">Implement a workflow client</span></span>  
  
1.  <span data-ttu-id="e0f66-129">Vytvořit nový projekt konzolové aplikace volá `Client`.</span><span class="sxs-lookup"><span data-stu-id="e0f66-129">Create a new console application project called `Client`.</span></span>  
  
2.  <span data-ttu-id="e0f66-130">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="e0f66-130">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="e0f66-131">Systém.</span><span class="sxs-lookup"><span data-stu-id="e0f66-131">System.Activities</span></span>  
  
    2.  <span data-ttu-id="e0f66-132">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e0f66-132">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="e0f66-133">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="e0f66-133">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="e0f66-134">Otevřete generovaný soubor Program.cs a přidejte statickou metodu s názvem `GetClientWorkflow` vytvoření pracovního postupu klienta.</span><span class="sxs-lookup"><span data-stu-id="e0f66-134">Open the generated Program.cs file and add a static method called `GetClientWorkflow` to create the client workflow.</span></span>  
  
    ```  
    static Activity GetClientWorkflow()  
    {  
       Variable<string> echoString = new Variable<string>();  
  
       Endpoint clientEndpoint = new Endpoint  
       {  
          Binding = new WSHttpBinding(SecurityMode.Message),  
          AddressUri = new Uri("http://localhost:8080/Service")  
       };  
  
       Send echoRequest = new Send  
       {  
          Endpoint = clientEndpoint,  
          ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
          OperationName = "Echo",  
          Content = new SendParametersContent()  
          {  
             Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
          }  
       };  
  
       return new Sequence  
       {  
          Variables = { echoString },  
          Activities =  
          {                      
             new CorrelationScope  
             {  
                Body = new Sequence  
                {  
                   Activities =   
                   {  
                      echoRequest,  
                      new ReceiveReply  
                      {  
                         Request = echoRequest,  
                         Content = new ReceiveParametersContent  
                         {  
                            Parameters = { { "result", new OutArgument<string>(echoString) } }  
                         }  
                      }  
                   }  
                }  
             },                      
             new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
             }  
          };  
       }  
    }  
    ```  
  
4.  <span data-ttu-id="e0f66-135">Přidejte následující hostování kód, který `Main()` metoda.</span><span class="sxs-lookup"><span data-stu-id="e0f66-135">Add the following hosting code to the `Main()` method.</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       Activity workflow = GetClientWorkflow();  
       WorkflowInvoker.Invoke(workflow);  
       WorkflowInvoker.Invoke(workflow);  
       Console.WriteLine("Press [ENTER] to exit");  
       Console.ReadLine();  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="e0f66-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0f66-136">Example</span></span>  
 <span data-ttu-id="e0f66-137">Tady je úplný zdrojový kód použitý v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="e0f66-137">Here is a complete listing of the source code used in this topic.</span></span>  
  
```  
// AccessIdentityCallback.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    class AccessIdentityCallback : IReceiveMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
        {  
            try  
            {  
                // Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                Console.WriteLine("Received a message from a workflow with the following identity" ); // with instanceId = {0}", instanceId);  
                Console.WriteLine("Windows Identity Name: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.Name);  
                Console.WriteLine("Windows Identity User: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.User);  
                Console.WriteLine("Windows Identity IsAuthenticated: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.IsAuthenticated);  
            }  
            catch (MessageHeaderException)  
            {  
                Console.WriteLine("This message must not be from a workflow.");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("An exception occurred: " + ex.Message);  
            }  
        }  
    }  
}  
```  
  
```  
// AccessIdentityScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public AccessIdentityScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex   
            metadata.AddImplementationVariable(this.currentIndex);  
        }                     
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("AccessIdentityCallback", new AccessIdentityCallback());  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```  
  
```  
// Service.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{      
    class Program  
    {  
        const string addr = "http://localhost:8080/Service";  
        static XName contract = XName.Get("IService", "http://tempuri.org");  
  
        static void Main(string[] args)  
        {  
            string addr = "http://localhost:8080/Service";  
  
            using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
            {  
                WSHttpBinding binding = new WSHttpBinding(SecurityMode.Message);  
                host.AddServiceEndpoint(contract, binding, addr);  
  
                host.Open();  
                Console.WriteLine("Service waiting at: " + addr);  
                Console.WriteLine("Press [ENTER] to exit");  
                Console.ReadLine();  
                host.Close();  
            }  
  
        }  
  
        static Activity GetServiceWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Receive echoRequest = new Receive  
            {  
                CanCreateInstance = true,  
                ServiceContractName = contract,  
                OperationName = "Echo",  
                Content = new ReceiveParametersContent()  
                {  
                    Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                }  
            };  
  
            return new AccessIdentityScope  
            {  
                Variables = { echoString },  
                Activities =  
                {  
                    echoRequest,  
                    new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                    new SendReply  
                    {  
                        Request = echoRequest,  
                        Content = new SendParametersContent()  
                        {  
                            Parameters = { { "result", new InArgument<string>(echoString) } }   
                        }  
                    }  
                }  
            };  
        }  
    }  
}  
```  
  
```  
// client.cs   
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Activity workflow = GetClientWorkflow();  
            WorkflowInvoker.Invoke(workflow);  
            WorkflowInvoker.Invoke(workflow);  
            Console.WriteLine("Press [ENTER] to exit");  
            Console.ReadLine();  
        }  
  
        static Activity GetClientWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Endpoint clientEndpoint = new Endpoint  
            {  
                Binding = new WSHttpBinding(SecurityMode.Message),  
                AddressUri = new Uri("http://localhost:8080/Service")  
            };  
  
            Send echoRequest = new Send  
            {  
                Endpoint = clientEndpoint,  
                ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                OperationName = "Echo",  
                Content = new SendParametersContent()  
                {  
                    Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                }  
            };  
  
            return new Sequence  
            {  
                Variables = { echoString },  
                Activities =  
                {                      
                    new CorrelationScope  
                    {  
                        Body = new Sequence  
                        {  
                            Activities =   
                            {  
                                echoRequest,  
                                new ReceiveReply  
                                {  
                                    Request = echoRequest,  
                                    Content = new ReceiveParametersContent  
                                    {  
                                        Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                    }  
                                }  
                            }  
                        }  
                    },                      
                    new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
                }  
            };  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0f66-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0f66-138">See Also</span></span>  
 [<span data-ttu-id="e0f66-139">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e0f66-139">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="e0f66-140">Přístup k OperationContext</span><span class="sxs-lookup"><span data-stu-id="e0f66-140">Accessing OperationContext</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [<span data-ttu-id="e0f66-141">Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu</span><span class="sxs-lookup"><span data-stu-id="e0f66-141">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
