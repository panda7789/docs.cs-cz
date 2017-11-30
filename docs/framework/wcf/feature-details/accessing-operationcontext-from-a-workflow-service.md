---
title: "Přístup k informacím OperationContext ze služby pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1dafe55-a20e-4db0-9ac8-90c315883cdd
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d18626412c0a6233c8792a4f19d5d05ef083333
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="accessing-operationcontext-from-a-workflow-service"></a><span data-ttu-id="edf27-102">Přístup k informacím OperationContext ze služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="edf27-102">Accessing OperationContext from a Workflow Service</span></span>
<span data-ttu-id="edf27-103">Pro přístup k <xref:System.ServiceModel.OperationContext> uvnitř služby pracovních postupů, je nutné implementovat <xref:System.ServiceModel.Activities.IReceiveMessageCallback> rozhraní pro provádění vlastní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="edf27-103">To access the <xref:System.ServiceModel.OperationContext> inside a workflow service, you must implement the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> interface in a custom execution property.</span></span> <span data-ttu-id="edf27-104">Přepsání <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> metoda, která se předá odkaz na <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="edf27-104">Override the <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)> method which is passed a reference to the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="edf27-105">Toto téma vás provede procesem implementace tato vlastnost provádění načíst vlastní hlavičky, jakož i vlastní aktivity, který bude surface této vlastnosti <xref:System.ServiceModel.Activities.Receive> za běhu.</span><span class="sxs-lookup"><span data-stu-id="edf27-105">This topic will walk you through implementing this execution property to retrieve a custom header, as well as a custom activity that will surface this property to the <xref:System.ServiceModel.Activities.Receive> at runtime.</span></span>  <span data-ttu-id="edf27-106">Vlastní aktivity budou implementovat stejné chování jako <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` aktivity, s výjimkou, že pokud <xref:System.ServiceModel.Activities.Receive> je umístěn uvnitř, <xref:System.ServiceModel.Activities.IReceiveMessageCallback> bude volána a <xref:System.ServiceModel.OperationContext> informace budou načteny.</span><span class="sxs-lookup"><span data-stu-id="edf27-106">The custom activity will implement the same behavior as a <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activity, except that when a <xref:System.ServiceModel.Activities.Receive> is placed inside of it, the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> will be called and the <xref:System.ServiceModel.OperationContext> information will be retrieved.</span></span>  <span data-ttu-id="edf27-107">Toto téma také ukazuje, jak získat přístup na straně klienta <xref:System.ServiceModel.OperationContext> přidat odchozí hlavičky prostřednictvím <xref:System.ServiceModel.Activities.ISendMessageCallback> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="edf27-107">This topic also shows how to access the client-side <xref:System.ServiceModel.OperationContext> to add outgoing headers via the <xref:System.ServiceModel.Activities.ISendMessageCallback> interface.</span></span>  
  
### <a name="implement-the-service-side-ireceivemessagecallback"></a><span data-ttu-id="edf27-108">Implementace IReceiveMessageCallback straně služby</span><span class="sxs-lookup"><span data-stu-id="edf27-108">Implement the Service-side IReceiveMessageCallback</span></span>  
  
1.  <span data-ttu-id="edf27-109">Vytvořte prázdnou [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] řešení.</span><span class="sxs-lookup"><span data-stu-id="edf27-109">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution.</span></span>  
  
2.  <span data-ttu-id="edf27-110">Přidejte novou aplikaci konzoly s názvem `Service` k řešení.</span><span class="sxs-lookup"><span data-stu-id="edf27-110">Add a new console application called `Service` to the solution.</span></span>  
  
3.  <span data-ttu-id="edf27-111">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="edf27-111">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="edf27-112">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="edf27-112">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="edf27-113">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edf27-113">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="edf27-114">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="edf27-114">System.ServiceModel.Activities</span></span>  
  
4.  <span data-ttu-id="edf27-115">Přidejte novou třídu s názvem `ReceiveInstanceIdCallback` a implementovat <xref:System.ServiceModel.Activities.IReceiveMessageCallback> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="edf27-115">Add a new class called `ReceiveInstanceIdCallback` and implement <xref:System.ServiceModel.Activities.IReceiveMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class ReceiveInstanceIdCallback : IReceiveMessageCallback  
    {  
          public const string HeaderName = "InstanceIdHeader";  
          public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
         public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
          {              
                try  
                {  
                    Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                    Console.WriteLine("Received a message from a workflow with instanceId = {0}", instanceId);  
                }  
                catch (MessageHeaderException)  
                {  
                    Console.WriteLine("This message must not be from a workflow.");  
                }  
            }  
    }  
    ```  
  
     <span data-ttu-id="edf27-116">Tento kód používá <xref:System.ServiceModel.OperationContext> předán do metody pro přístup k hlavičky příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="edf27-116">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to access the incoming message’s headers.</span></span>  
  
### <a name="implement-a-service-side-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="edf27-117">Implementace aktivitu nativní straně služby pro přidání do NativeActivityContext IReceiveMessageCallback implementace</span><span class="sxs-lookup"><span data-stu-id="edf27-117">Implement a Service-side Native activity to add the IReceiveMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="edf27-118">Přidání nové třídy odvozené od <xref:System.Activities.NativeActivity> názvem `ReceiveInstanceIdScope`.</span><span class="sxs-lookup"><span data-stu-id="edf27-118">Add a new class derived from <xref:System.Activities.NativeActivity> called `ReceiveInstanceIdScope`.</span></span>  
  
2.  <span data-ttu-id="edf27-119">Přidejte ke sledování podřízené aktivity, proměnné, index aktuální aktivity, místní proměnné a <xref:System.Activities.CompletionCallback> zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="edf27-119">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class ReceiveInstanceIdScope : NativeActivity  
        {  
            Collection<Activity> children;  
            Collection<Variable> variables;  
            Variable<int> currentIndex;  
            CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="edf27-120">Implementace konstruktoru</span><span class="sxs-lookup"><span data-stu-id="edf27-120">Implement the constructor</span></span>  
  
    ```  
    public ReceiveInstanceIdScope()  
                : base()  
            {  
                this.children = new Collection<Activity>();  
                this.variables = new Collection<Variable>();  
                this.currentIndex = new Variable<int>();  
            }  
    }  
    ```  
  
4.  <span data-ttu-id="edf27-121">Implementace `Activities` a `Variables` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="edf27-121">Implement the `Activities` and `Variables` properties.</span></span>  
  
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
  
5.  <span data-ttu-id="edf27-122">Přepsání<xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="edf27-122">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="edf27-123">Přepsání<xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="edf27-123">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
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
  
### <a name="implement-the-workflow-service"></a><span data-ttu-id="edf27-124">Implementace služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="edf27-124">Implement the workflow service</span></span>  
  
1.  <span data-ttu-id="edf27-125">Otevřete existující `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="edf27-125">Open the existing `Program` class.</span></span>  
  
2.  <span data-ttu-id="edf27-126">Definujte následující konstanty:</span><span class="sxs-lookup"><span data-stu-id="edf27-126">Define the following constants:</span></span>  
  
    ```  
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  <span data-ttu-id="edf27-127">Přidat statickou metodu s názvem `GetWorkflowService` vytvářející služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="edf27-127">Add a static method called `GetWorkflowService` that creates the workflow service.</span></span>  
  
    ```  
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
  
                return new ReceiveInstanceIdScope  
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
  
4.  <span data-ttu-id="edf27-128">Ve stávající `Main` metoda hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="edf27-128">In the existing `Main` method, host the workflow service.</span></span>  
  
    ```  
    static void Main(string[] args)  
            {  
                string addr = "http://localhost:8080/Service";  
  
                using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
                {  
                    host.AddServiceEndpoint(contract, new BasicHttpBinding(), addr);  
  
                    host.Open();  
                    Console.WriteLine("Service waiting at: " + addr);  
                    Console.WriteLine("Press [ENTER] to exit");  
                    Console.ReadLine();  
                    host.Close();  
                }  
            }  
    ```  
  
### <a name="implement-the-client-side-isendmessagecallback"></a><span data-ttu-id="edf27-129">Implementace ISendMessageCallback na straně klienta</span><span class="sxs-lookup"><span data-stu-id="edf27-129">Implement the Client-side ISendMessageCallback</span></span>  
  
1.  <span data-ttu-id="edf27-130">Přidejte novou aplikaci konzoly s názvem `Service` k řešení.</span><span class="sxs-lookup"><span data-stu-id="edf27-130">Add a new console application called `Service` to the solution.</span></span>  
  
2.  <span data-ttu-id="edf27-131">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="edf27-131">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="edf27-132">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="edf27-132">System.Runtime.Serialization</span></span>  
  
    2.  <span data-ttu-id="edf27-133">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edf27-133">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="edf27-134">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="edf27-134">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="edf27-135">Přidejte novou třídu s názvem `SendInstanceIdCallback` a implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="edf27-135">Add a new class called `SendInstanceIdCallback` and implement <xref:System.ServiceModel.Activities.ISendMessageCallback> as shown in the following example.</span></span>  
  
    ```csharp  
    class SendInstanceIdCallback : ISendMessageCallback  
        {  
            public const string HeaderName = "InstanceIdHeader";  
            public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
            public Guid InstanceId { get; set; }  
  
            public void OnSendMessage(System.ServiceModel.OperationContext operationContext)  
            {  
                operationContext.OutgoingMessageHeaders.Add(MessageHeader.CreateHeader(HeaderName, HeaderNS, this.InstanceId));  
            }  
        }  
    ```  
  
     <span data-ttu-id="edf27-136">Tento kód používá <xref:System.ServiceModel.OperationContext> předaný do metody přidat vlastní hlavičku pro příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="edf27-136">This code uses the <xref:System.ServiceModel.OperationContext> passed into the method to add a custom header to the incoming message.</span></span>  
  
### <a name="implement-a-client-side-native-activity-to-add-the-client-side-isendmessagecallback-implementation-to-the-nativeactivitycontext"></a><span data-ttu-id="edf27-137">Implementace aktivitu nativní straně klienta pro přidání do NativeActivityContext implementace ISendMessageCallback straně klienta</span><span class="sxs-lookup"><span data-stu-id="edf27-137">Implement a Client-side Native activity to add the client-side ISendMessageCallback implementation to the NativeActivityContext</span></span>  
  
1.  <span data-ttu-id="edf27-138">Přidání nové třídy odvozené od <xref:System.Activities.NativeActivity> názvem `SendInstanceIdScope`.</span><span class="sxs-lookup"><span data-stu-id="edf27-138">Add a new class derived from <xref:System.Activities.NativeActivity> called `SendInstanceIdScope`.</span></span>  
  
2.  <span data-ttu-id="edf27-139">Přidejte ke sledování podřízené aktivity, proměnné, index aktuální aktivity, místní proměnné a <xref:System.Activities.CompletionCallback> zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="edf27-139">Add local variables to keep track of child activities, variables, current activity index, and a <xref:System.Activities.CompletionCallback> callback.</span></span>  
  
    ```  
    public sealed class SendInstanceIdScope : NativeActivity  
        {  
            Collection<Activity> children;  
            Collection<Variable> variables;  
            Variable<int> currentIndex;  
            CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  <span data-ttu-id="edf27-140">Implementace konstruktoru</span><span class="sxs-lookup"><span data-stu-id="edf27-140">Implement the constructor</span></span>  
  
    ```  
    public SendInstanceIdScope()  
                : base()  
            {  
                this.children = new Collection<Activity>();  
                this.variables = new Collection<Variable>();  
                this.currentIndex = new Variable<int>();  
            }  
    ```  
  
4.  <span data-ttu-id="edf27-141">Implementace `Activities` a `Variables` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="edf27-141">Implement the `Activities` and `Variables` properties.</span></span>  
  
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
  
5.  <span data-ttu-id="edf27-142">Přepsání<xref:System.Activities.NativeActivity.CacheMetadata%2A></span><span class="sxs-lookup"><span data-stu-id="edf27-142">Override <xref:System.Activities.NativeActivity.CacheMetadata%2A></span></span>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  <span data-ttu-id="edf27-143">Přepsání<xref:System.Activities.NativeActivity.Execute%2A></span><span class="sxs-lookup"><span data-stu-id="edf27-143">Override <xref:System.Activities.NativeActivity.Execute%2A></span></span>  
  
    ```  
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("SendInstanceIdCallback", new SendInstanceIdCallback() { InstanceId = context.WorkflowInstanceId });  
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
    protected override void Execute(  
                NativeActivityContext context)  
            {  
                context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
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
  
### <a name="implement-a-workflow-client"></a><span data-ttu-id="edf27-144">Implementace klienta pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="edf27-144">Implement a workflow client</span></span>  
  
1.  <span data-ttu-id="edf27-145">Vytvořit nový projekt konzolové aplikace volá `Client`.</span><span class="sxs-lookup"><span data-stu-id="edf27-145">Create a new console application project called `Client`.</span></span>  
  
2.  <span data-ttu-id="edf27-146">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="edf27-146">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="edf27-147">Systém.</span><span class="sxs-lookup"><span data-stu-id="edf27-147">System.Activities</span></span>  
  
    2.  <span data-ttu-id="edf27-148">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edf27-148">System.ServiceModel</span></span>  
  
    3.  <span data-ttu-id="edf27-149">System.ServiceModel.Activities</span><span class="sxs-lookup"><span data-stu-id="edf27-149">System.ServiceModel.Activities</span></span>  
  
3.  <span data-ttu-id="edf27-150">Otevřete generovaný soubor Program.cs a přidejte statickou metodu s názvem `GetClientWorkflow` vytvoření pracovního postupu klienta.</span><span class="sxs-lookup"><span data-stu-id="edf27-150">Open the generated Program.cs file and add a static method called `GetClientWorkflow` to create the client workflow.</span></span>  
  
    ```  
    static Activity GetClientWorkflow()  
            {  
                Variable<string> echoString = new Variable<string>();  
  
                // Define the endpoint  
                Endpoint clientEndpoint = new Endpoint  
                {  
                    Binding = new BasicHttpBinding(),  
                    AddressUri = new Uri("http://localhost:8080/Service")  
                };  
  
                // Configure the Send activity used to send a message  
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
  
                // Place the Send activity in a SendInstanceIdScope. This hooks up the ISendMessageCallback   
                // implementation to the client workflow.  
                return new SendInstanceIdScope  
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
                                    // Send the request message  
                                    echoRequest,  
  
                                   // Receive the reply from the service  
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
    ```  
  
4.  <span data-ttu-id="edf27-151">Přidejte následující hostování kód, který `Main()` metoda.</span><span class="sxs-lookup"><span data-stu-id="edf27-151">Add the following hosting code to the `Main()` method.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="edf27-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="edf27-152">Example</span></span>  
 <span data-ttu-id="edf27-153">Tady je úplný zdrojový kód použitý v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="edf27-153">Here is a complete listing of the source code used in this topic.</span></span>  
  
```  
// ReceiveInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    public sealed class ReceiveInstanceIdScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public ReceiveInstanceIdScope()  
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
            context.Properties.Add("ReceiveInstanceIdCallback", new ReceiveInstanceIdCallback());  
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
// ReceiveInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    class ReceiveInstanceIdCallback : IReceiveMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
        {              
            try  
            {  
                Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                Console.WriteLine("Received a message from a workflow with instanceId = {0}", instanceId);  
            }  
            catch (MessageHeaderException)  
            {  
                Console.WriteLine("This message must not be from a workflow.");  
            }  
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
                host.AddServiceEndpoint(contract, new BasicHttpBinding(), addr);  
  
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
  
            return new ReceiveInstanceIdScope  
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
// SendInstanceIdCallback.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class SendInstanceIdCallback : ISendMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public Guid InstanceId { get; set; }  
  
        public void OnSendMessage(System.ServiceModel.OperationContext operationContext)  
        {  
            operationContext.OutgoingMessageHeaders.Add(MessageHeader.CreateHeader(HeaderName, HeaderNS, this.InstanceId));  
        }  
    }  
}  
```  
  
```  
// SendInstanceIdScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    public sealed class SendInstanceIdScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public SendInstanceIdScope()  
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
            context.Properties.Add("SendInstanceIdCallback", new SendInstanceIdCallback() { InstanceId = context.WorkflowInstanceId });  
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
// Client.cs  
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
                Binding = new BasicHttpBinding(),  
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
  
            return new SendInstanceIdScope  
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
  
 <span data-ttu-id="edf27-154">Volitelné komentáře.</span><span class="sxs-lookup"><span data-stu-id="edf27-154">Optional comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf27-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="edf27-155">See Also</span></span>  
 [<span data-ttu-id="edf27-156">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="edf27-156">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="edf27-157">Přístup k informacím OperationContext</span><span class="sxs-lookup"><span data-stu-id="edf27-157">Accessing OperationContext</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [<span data-ttu-id="edf27-158">Vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kódu</span><span class="sxs-lookup"><span data-stu-id="edf27-158">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
