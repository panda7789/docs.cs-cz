---
title: 'Postupy: hostování bez služby pracovního postupu ve službě IIS'
ms.date: 03/30/2017
ms.assetid: f362562c-767d-401b-8257-916616568fd4
ms.openlocfilehash: 70fd6aca94f2addd7ee568e897171ae1da86db67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496748"
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a><span data-ttu-id="41fb0-102">Postupy: hostování bez služby pracovního postupu ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="41fb0-102">How to: Host a non-service workflow in IIS</span></span>
<span data-ttu-id="41fb0-103">Pracovní postupy, které nejsou služby pracovního postupu může být hostovaný v rámci služby IIS / byla.</span><span class="sxs-lookup"><span data-stu-id="41fb0-103">Workflows that are not workflow services can be hosted under IIS/WAS.</span></span> <span data-ttu-id="41fb0-104">To je užitečné, pokud budete potřebovat k hostování pracovní postup zapsaných správcem někdo jiný.</span><span class="sxs-lookup"><span data-stu-id="41fb0-104">This is useful when you need to host a workflow written by somebody else.</span></span> <span data-ttu-id="41fb0-105">Například pokud opětovným hostováním návrháře pracovních postupů a povolit uživatelům vytvářet své vlastní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-105">For example, if you rehost the workflow designer and allow users to create their own workflows.</span></span>  <span data-ttu-id="41fb0-106">Hostování pracovních bez služby ve službě IIS poskytuje podporu pro funkce, například recyklace, nečinnosti ukončení procesu, monitorování stavu procesu a aktivaci na základě zpráv.</span><span class="sxs-lookup"><span data-stu-id="41fb0-106">Hosting non-service workflows in IIS provides support for features like process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="41fb0-107">Pracovní postup služby hostované ve službě IIS obsahovat <xref:System.ServiceModel.Activities.Receive> aktivity a jsou aktivovat, pokud služba IIS přijme zprávu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-107">Workflow services hosted in IIS contain <xref:System.ServiceModel.Activities.Receive> activities and are activated when a message is received by IIS.</span></span> <span data-ttu-id="41fb0-108">Jiné než služba pracovní postupy neobsahují aktivity zasílání zpráv a ve výchozím nastavení nelze aktivovat odesláním zprávy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-108">Non-service workflows do not contain messaging activities, and by default cannot be activated by sending a message.</span></span>  <span data-ttu-id="41fb0-109">Musí být odvozen od třídy <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> a definování kontraktu služby, který obsahuje operace vytvoření instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-109">You must derive a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> and define a service contract that contains operations to create an instance of the workflow.</span></span> <span data-ttu-id="41fb0-110">Toto téma vás provede procesem vytvoření jednoduchého pracovního postupu, definování kontraktu služby klienta můžete použít k aktivaci pracovního postupu a odvození třídy z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , který používá kontrakt služby tak, aby naslouchala pro vytváření žádostí o pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="41fb0-110">This topic will walk you through creating a simple workflow, defining a service contract a client can use to activate the workflow, and deriving a class from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> which uses the service contract to listen for workflow creating requests.</span></span>  
  
### <a name="create-a-simple-workflow"></a><span data-ttu-id="41fb0-111">Vytvoření jednoduchého pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="41fb0-111">Create a simple workflow</span></span>  
  
1.  <span data-ttu-id="41fb0-112">Vytvořte novou [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prázdný řešení názvem `CreationEndpointTest`.</span><span class="sxs-lookup"><span data-stu-id="41fb0-112">Create a new [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] empty solution called `CreationEndpointTest`.</span></span>  
  
2.  <span data-ttu-id="41fb0-113">Přidat nový projekt aplikace pracovního postupu služby WCF s názvem `SimpleWorkflow` k řešení.</span><span class="sxs-lookup"><span data-stu-id="41fb0-113">Add a new WCF Workflow Service Application project called `SimpleWorkflow` to the solution.</span></span> <span data-ttu-id="41fb0-114">Otevře se návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="41fb0-114">The workflow designer will open.</span></span>  
  
3.  <span data-ttu-id="41fb0-115">Odstraníte ReceiveRequest a SendResponse aktivity.</span><span class="sxs-lookup"><span data-stu-id="41fb0-115">Delete the ReceiveRequest and SendResponse activities.</span></span> <span data-ttu-id="41fb0-116">Tyto aktivity jsou díky pracovní postup služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="41fb0-116">These activities are what makes a workflow a workflow service.</span></span> <span data-ttu-id="41fb0-117">Vzhledem k tomu, že jsme nefungují s služby pracovního postupu, jsme již nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="41fb0-117">Since we are not working with a workflow service, we no longer need them.</span></span>  
  
4.  <span data-ttu-id="41fb0-118">Nastavte DisplayName aktivity pořadí "Sekvenčního pracovního postupu".</span><span class="sxs-lookup"><span data-stu-id="41fb0-118">Set the DisplayName for the sequence activity to "Sequential Workflow".</span></span>  
  
5.  <span data-ttu-id="41fb0-119">Přejmenujte Service1.xamlx Workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="41fb0-119">Rename Service1.xamlx to Workflow1.xamlx.</span></span>  
  
6.  <span data-ttu-id="41fb0-120">Klikněte na tlačítko návrháře mimo pořadí aktivity a nastavte vlastnosti Name a ConfigurationName na "Workflow1"</span><span class="sxs-lookup"><span data-stu-id="41fb0-120">Click the designer outside of the sequence activity, and set the Name and ConfigurationName properties to "Workflow1"</span></span>  
  
7.  <span data-ttu-id="41fb0-121">Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivity do <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="41fb0-121">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence>.</span></span> <span data-ttu-id="41fb0-122"><xref:System.Activities.Statements.WriteLine> Aktivity naleznete v **primitiv** oddílu na panelu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-122">The <xref:System.Activities.Statements.WriteLine> activity can be found in the **Primitives** section of the toolbox.</span></span> <span data-ttu-id="41fb0-123">Nastavte <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost <xref:System.Activities.Statements.WriteLine> se aktivita "Hello, world".</span><span class="sxs-lookup"><span data-stu-id="41fb0-123">Set the <xref:System.Activities.Statements.WriteLine.Text%2A> property of the <xref:System.Activities.Statements.WriteLine> activity to "Hello, world".</span></span>  
  
     <span data-ttu-id="41fb0-124">Pracovní postup by teď měl vypadat podobně jako v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-124">The workflow should now look like the following diagram.</span></span>  
  
     <span data-ttu-id="41fb0-125">![Jednoduché pracovního postupu](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span><span class="sxs-lookup"><span data-stu-id="41fb0-125">![A simple workflow](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")</span></span>  
  
### <a name="create-the-workflow-creation-service-contract"></a><span data-ttu-id="41fb0-126">Vytvoření kontraktu služby vytvoření pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="41fb0-126">Create the workflow creation service contract</span></span>  
  
1.  <span data-ttu-id="41fb0-127">Přidat nový projekt knihovny třídy s názvem `Shared` k `CreationEndpointTest` řešení.</span><span class="sxs-lookup"><span data-stu-id="41fb0-127">Add a new class library project called `Shared` to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="41fb0-128">Přidat odkaz na System.ServiceModel.dll System.Configuration a System.ServiceModel.Activities k `Shared` projektu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-128">Add a reference to System.ServiceModel.dll, System.Configuration, and System.ServiceModel.Activities to the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="41fb0-129">Přejmenujte soubor Class1.cs IWorkflowCreation.cs a následující kód do souboru.</span><span class="sxs-lookup"><span data-stu-id="41fb0-129">Rename the Class1.cs file to IWorkflowCreation.cs and the following code to the file.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     <span data-ttu-id="41fb0-130">Tento kontrakt definuje dvě operace, jak vytvořit novou instanci pracovního postupu bez služby, kterou jste právě vytvořili.</span><span class="sxs-lookup"><span data-stu-id="41fb0-130">This contract defines two operations both create a new instance of the non-service workflow you just created.</span></span> <span data-ttu-id="41fb0-131">Jeden vytvoří novou instanci s ID generovaného instance a dalších umožňuje zadat ID instance pro nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-131">One creates a new instance with a generated instance ID and the other allows you to specify the instance ID for the new workflow instance.</span></span>  <span data-ttu-id="41fb0-132">Obě metody umožňují předat parametry do nové instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-132">Both methods allow you to pass in parameters to the new workflow instance.</span></span> <span data-ttu-id="41fb0-133">Tento kontrakt budou vystavené <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> tak, aby klienti k vytvoření nové instance pracovního postupu jiné služby.</span><span class="sxs-lookup"><span data-stu-id="41fb0-133">This contract will be exposed by the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to allow clients to create new instances of a non-service workflow.</span></span>  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a><span data-ttu-id="41fb0-134">Odvození třídy z WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="41fb0-134">Derive a class from WorkflowHostingEndpoint</span></span>  
  
1.  <span data-ttu-id="41fb0-135">Přidejte novou třídu s názvem `CreationEndpoint` odvozené z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k `Shared` projektu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-135">Add a new class called `CreationEndpoint` derived from <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to the `Shared` project.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  <span data-ttu-id="41fb0-136">Přidat místní statického <xref:System.Uri> proměnné s názvem `defaultBaseUri` k `CreationEndpoint` třídy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-136">Add a local static <xref:System.Uri> variable called `defaultBaseUri` to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  <span data-ttu-id="41fb0-137">Přidejte následující konstruktor `CreationEndpoint` třídy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-137">Add the following constructor to the `CreationEndpoint` class.</span></span> <span data-ttu-id="41fb0-138">Všimněte si určíme `IWorkflowCreation` kontraktu služby ve volání základní konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="41fb0-138">Notice we specify the `IWorkflowCreation` service contract in the call to the base constructor.</span></span>  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  <span data-ttu-id="41fb0-139">Přidejte následující konstruktor výchozí `CreationEndpoint` třídy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-139">Add the following default constructor to the `CreationEndpoint` class.</span></span>  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  <span data-ttu-id="41fb0-140">Přidání statického `DefaultBaseUri` vlastnost, která má `CreationEndpoint` třídy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-140">Add a static `DefaultBaseUri` property to the `CreationEndpoint` class.</span></span> <span data-ttu-id="41fb0-141">Tato vlastnost slouží k uložení výchozí základní identifikátor URI, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="41fb0-141">This property will be used to hold a default base URI if one is not provided.</span></span>  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  <span data-ttu-id="41fb0-142">Vytvořte následující metodu k získání výchozí vazby má použít pro vytvoření koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-142">Create the following method to get the default binding to use for the creation endpoint.</span></span>  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  <span data-ttu-id="41fb0-143">Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> metoda vrátí ID instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="41fb0-143">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> method to return the workflow instance ID.</span></span> <span data-ttu-id="41fb0-144">Pokud `Action` záhlaví končí "Vytvořit" vrátí prázdný identifikátor GUID, pokud `Action` záhlaví končí textem "CreateWithInstanceId" vrátí identifikátor GUID předán do metody.</span><span class="sxs-lookup"><span data-stu-id="41fb0-144">If the `Action` header ends with "Create" return an empty GUID, if the `Action` header ends with "CreateWithInstanceId" return the GUID passed into the method.</span></span> <span data-ttu-id="41fb0-145">Jinak, throw <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="41fb0-145">Otherwise, throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="41fb0-146">Tyto `Action` hlavičky odpovídají těchto dvou operací, které jsou definované v `IWorkflowCreation` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="41fb0-146">These `Action` headers correspond to the two operations defined in the `IWorkflowCreation` service contract.</span></span>  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  <span data-ttu-id="41fb0-147">Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> metodu pro vytvoření <xref:System.ServiceModel.Activities.WorkflowCreationContext> a přidat všechny argumenty pro pracovní postup, odeslání instance ID do klienta a pak se vraťte <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span><span class="sxs-lookup"><span data-stu-id="41fb0-147">Override the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> method to create a <xref:System.ServiceModel.Activities.WorkflowCreationContext> and add any arguments for the workflow, send the instance ID to the client, and then return the <xref:System.ServiceModel.Activities.WorkflowCreationContext>.</span></span>  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a><span data-ttu-id="41fb0-148">Vytvořit element standardní koncový bod a umožní vám nakonfigurovat WorkflowCreationEndpoint</span><span class="sxs-lookup"><span data-stu-id="41fb0-148">Create a standard endpoint element to allow you to configure the WorkflowCreationEndpoint</span></span>  
  
1.  <span data-ttu-id="41fb0-149">Přidat odkaz na sdílené v `CreationEndpoint` projektu</span><span class="sxs-lookup"><span data-stu-id="41fb0-149">Add a reference to Shared in the `CreationEndpoint` project</span></span>  
  
2.  <span data-ttu-id="41fb0-150">Přidejte novou třídu s názvem `CreationEndpointElement`, odvozené z <xref:System.ServiceModel.Configuration.StandardEndpointElement> k `CreationEndpoint` projektu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-150">Add a new class called `CreationEndpointElement`, derived from <xref:System.ServiceModel.Configuration.StandardEndpointElement> to the `CreationEndpoint` project.</span></span> <span data-ttu-id="41fb0-151">Tato třída bude reprezentovat `CreationEndpoint` v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="41fb0-151">This class will represent a `CreationEndpoint` in a web.config file.</span></span>  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  <span data-ttu-id="41fb0-152">Přidat vlastnost s názvem `EndpointType` k návratový typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-152">Add a property called `EndpointType` to return the type of the endpoint.</span></span>  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  <span data-ttu-id="41fb0-153">Přepsání <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> metoda a vraťte se a nové `CreationEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="41fb0-153">Override the <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> method and return a new `CreationEndpoint`.</span></span>  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  <span data-ttu-id="41fb0-154">Přetížení <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, a <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="41fb0-154">Overload the <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, and <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> methods.</span></span> <span data-ttu-id="41fb0-155">Tyto metody právě musí být definované, není nutné přidat žádný kód k nim.</span><span class="sxs-lookup"><span data-stu-id="41fb0-155">These methods just need to be defined, you do not need to add any code to them.</span></span>  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  <span data-ttu-id="41fb0-156">Přidejte třídu kolekce pro `CreationEndpoint` do souboru CreationEndpointElement.cs v `CreationEndpoint` projektu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-156">Add the collection class for `CreationEndpoint` to the CreationEndpointElement.cs file in the `CreationEndpoint` project.</span></span> <span data-ttu-id="41fb0-157">Tato třída se používá v konfiguraci k uložení několika `CreationEndpoint` instance v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="41fb0-157">This class is used by configuration to hold a number of `CreationEndpoint` instances in a web.config file.</span></span>  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="41fb0-158">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="41fb0-158">Build the solution.</span></span>  
  
### <a name="host-the-workflow-in-iis"></a><span data-ttu-id="41fb0-159">Hostitele pracovního postupu ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="41fb0-159">Host the workflow in IIS</span></span>  
  
1.  <span data-ttu-id="41fb0-160">Vytvořit novou aplikaci s názvem `MyCreationEndpoint` ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="41fb0-160">Create a new application called `MyCreationEndpoint` in IIS.</span></span>  
  
2.  <span data-ttu-id="41fb0-161">Zkopírujte soubor workflow1.xaml generované návrháře pracovních postupů k adresáři aplikace a přejmenujte jej na workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="41fb0-161">Copy the workflow1.xaml file generated by the workflow designer to the application directory and rename it to workflow1.xamlx.</span></span>  
  
3.  <span data-ttu-id="41fb0-162">Kopírovat shared.dll a CreationEndpoint.dll soubory do adresáře bin aplikace (vytvořit adresář bin, pokud není přítomen).</span><span class="sxs-lookup"><span data-stu-id="41fb0-162">Copy the shared.dll and CreationEndpoint.dll files to the application’s bin directory (create the bin directory if it is not present).</span></span>  
  
4.  <span data-ttu-id="41fb0-163">Nahraďte obsah souboru Web.config v `CreationEndpoint` projektu s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="41fb0-163">Replace the contents of the Web.config file in the `CreationEndpoint` project with the following code.</span></span>  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  <span data-ttu-id="41fb0-164">Po `<system.web>` elementu, registrace `CreationEndpoint` přidáním následujícího kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="41fb0-164">After the `<system.web>` element, register `CreationEndpoint` by adding the following configuration code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="41fb0-165">Takovém postupu zaregistruje `CreationEndpointCollection` třídy, můžete nakonfigurovat `CreationEndpoint` v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="41fb0-165">This registers the `CreationEndpointCollection` class so you can configure a `CreationEndpoint` in a web.config file.</span></span>  
  
6.  <span data-ttu-id="41fb0-166">Přidat `<service>` – element (po \</extensions > značka) s `CreationEndpoint` bude naslouchat příchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="41fb0-166">Add a `<service>` element (after the \</extensions> tag) with a `CreationEndpoint` which will listen for incoming messages.</span></span>  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  <span data-ttu-id="41fb0-167">Přidat \<chování > elementu (po  \< /služby > značka) umožňující metadata služby.</span><span class="sxs-lookup"><span data-stu-id="41fb0-167">Add a \<behaviors> element (after the \</services> tag) to enable service metadata.</span></span>  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  <span data-ttu-id="41fb0-168">Zkopírujte soubor web.config do adresáře aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="41fb0-168">Copy the web.config to your IIS application directory.</span></span>  
  
9. <span data-ttu-id="41fb0-169">Test ke zjištění, zda vytvoření koncového bodu pracuje kliknutím spuštění aplikace Internet Explorer a přejděte na http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="41fb0-169">Test to see if the creation endpoint is working by starting Internet Explorer and browsing to http://localhost/MyCreationEndpoint/Workflow1.xamlx.</span></span> <span data-ttu-id="41fb0-170">Internet Explorer musí zobrazí následující obrazovka:</span><span class="sxs-lookup"><span data-stu-id="41fb0-170">Internet Explorer should display the following screen:</span></span>  
  
     <span data-ttu-id="41fb0-171">![Testování služby](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span><span class="sxs-lookup"><span data-stu-id="41fb0-171">![Testing the service](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")</span></span>  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a><span data-ttu-id="41fb0-172">Vytvořte klienta, která bude volat CreationEndpoint.</span><span class="sxs-lookup"><span data-stu-id="41fb0-172">Create a client that will call the CreationEndpoint.</span></span>  
  
1.  <span data-ttu-id="41fb0-173">Přidat novou konzolovou aplikaci do `CreationEndpointTest` řešení.</span><span class="sxs-lookup"><span data-stu-id="41fb0-173">Add a new Console application to the `CreationEndpointTest` solution.</span></span>  
  
2.  <span data-ttu-id="41fb0-174">Přidejte odkazy na System.ServiceModel.dll, System.ServiceModel.Activities a `Shared` projektu.</span><span class="sxs-lookup"><span data-stu-id="41fb0-174">Add references to System.ServiceModel.dll, System.ServiceModel.Activities, and the `Shared` project.</span></span>  
  
3.  <span data-ttu-id="41fb0-175">V `Main` metoda vytvoření <xref:System.ServiceModel.ChannelFactory%601> typu `IWorkflowCreation` a volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span><span class="sxs-lookup"><span data-stu-id="41fb0-175">In the `Main` method create a <xref:System.ServiceModel.ChannelFactory%601> of type `IWorkflowCreation` and call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>.</span></span> <span data-ttu-id="41fb0-176">Tato možnost vrátí proxy server.</span><span class="sxs-lookup"><span data-stu-id="41fb0-176">This will return a proxy.</span></span> <span data-ttu-id="41fb0-177">Potom můžete volat `Create` na zda proxy serveru k vytvoření instance pracovního postupu hostované v rámci služby IIS:</span><span class="sxs-lookup"><span data-stu-id="41fb0-177">You can then call `Create` on that proxy to create the workflow instance hosted under IIS:</span></span>  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="41fb0-178">Spusťte CreationEndpointClient.</span><span class="sxs-lookup"><span data-stu-id="41fb0-178">Run the CreationEndpointClient.</span></span> <span data-ttu-id="41fb0-179">Výstup by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="41fb0-179">The output should look like the following:</span></span>  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="41fb0-180">Neuvidíte výstup pracovního postupu, protože je spuštěna v rámci služby IIS, který nemá žádný výstup konzoly.</span><span class="sxs-lookup"><span data-stu-id="41fb0-180">You will not see the output of the workflow because it is running under IIS which has no console output.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41fb0-181">Příklad</span><span class="sxs-lookup"><span data-stu-id="41fb0-181">Example</span></span>  
 <span data-ttu-id="41fb0-182">Následuje kompletní kód této ukázce.</span><span class="sxs-lookup"><span data-stu-id="41fb0-182">The following is the complete code for this sample.</span></span>  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 <span data-ttu-id="41fb0-183">V tomto příkladu může zdát matoucí, protože nikdy implementovat služba, která implementuje `IWorkflowCreation`.</span><span class="sxs-lookup"><span data-stu-id="41fb0-183">This example may seem confusing because you never implement a service that implements `IWorkflowCreation`.</span></span> <span data-ttu-id="41fb0-184">Důvodem je, že `CreationEndpoint` nemá to pro vás.</span><span class="sxs-lookup"><span data-stu-id="41fb0-184">This is because the `CreationEndpoint` does this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41fb0-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="41fb0-185">See Also</span></span>  
 [<span data-ttu-id="41fb0-186">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="41fb0-186">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="41fb0-187">Hostování v Internetové informační službě</span><span class="sxs-lookup"><span data-stu-id="41fb0-187">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="41fb0-188">Osvědčené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="41fb0-188">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="41fb0-189">Pokyny k hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="41fb0-189">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="41fb0-190">Architektura Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="41fb0-190">Windows Workflow Architecture</span></span>](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [<span data-ttu-id="41fb0-191">Záložka pro obnovení WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="41fb0-191">WorkflowHostingEndpoint Resume Bookmark</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [<span data-ttu-id="41fb0-192">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="41fb0-192">Rehosting the Workflow Designer</span></span>](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="41fb0-193">Přehled Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="41fb0-193">Windows Workflow Overview</span></span>](../../../../docs/framework/windows-workflow-foundation/overview.md)
