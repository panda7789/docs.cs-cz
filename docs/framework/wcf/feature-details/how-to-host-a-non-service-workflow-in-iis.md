---
title: "Postupy: hostování bez služby pracovního postupu ve službě IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362562c-767d-401b-8257-916616568fd4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 892875fb8340220dc152f91ab2239257c7b96fb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a>Postupy: hostování bez služby pracovního postupu ve službě IIS
Pracovní postupy, které nejsou služby pracovního postupu může být hostovaný v rámci služby IIS / byla. To je užitečné, pokud budete potřebovat k hostování pracovní postup zapsaných správcem někdo jiný. Například pokud opětovným hostováním návrháře pracovních postupů a povolit uživatelům vytvářet své vlastní pracovní postupy.  Hostování pracovních bez služby ve službě IIS poskytuje podporu pro funkce, například recyklace, nečinnosti ukončení procesu, monitorování stavu procesu a aktivaci na základě zpráv. Pracovní postup služby hostované ve službě IIS obsahovat <xref:System.ServiceModel.Activities.Receive> aktivity a jsou aktivovat, pokud služba IIS přijme zprávu. Jiné než služba pracovní postupy neobsahují aktivity zasílání zpráv a ve výchozím nastavení nelze aktivovat odesláním zprávy.  Musí být odvozen od třídy <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> a definování kontraktu služby, který obsahuje operace vytvoření instance pracovního postupu. Toto téma vás provede procesem vytvoření jednoduchého pracovního postupu, definování kontraktu služby klienta můžete použít k aktivaci pracovního postupu a odvození třídy z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> , který používá kontrakt služby tak, aby naslouchala pro vytváření žádostí o pracovní postup.  
  
### <a name="create-a-simple-workflow"></a>Vytvoření jednoduchého pracovního postupu  
  
1.  Vytvořte novou [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prázdný řešení názvem `CreationEndpointTest`.  
  
2.  Přidat nový projekt aplikace pracovního postupu služby WCF s názvem `SimpleWorkflow` k řešení. Otevře se návrháře pracovních postupů.  
  
3.  Odstraníte ReceiveRequest a SendResponse aktivity. Tyto aktivity jsou díky pracovní postup služby pracovních postupů. Vzhledem k tomu, že jsme nefungují s služby pracovního postupu, jsme již nepotřebujete.  
  
4.  Nastavte DisplayName aktivity pořadí "Sekvenčního pracovního postupu".  
  
5.  Přejmenujte Service1.xamlx Workflow1.xamlx.  
  
6.  Klikněte na tlačítko návrháře mimo pořadí aktivity a nastavte vlastnosti Name a ConfigurationName na "Workflow1"  
  
7.  Přetáhněte <xref:System.Activities.Statements.WriteLine> aktivity do <xref:System.Activities.Statements.Sequence>. <xref:System.Activities.Statements.WriteLine> Aktivity naleznete v **primitiv** oddílu na panelu. Nastavte <xref:System.Activities.Statements.WriteLine.Text%2A> vlastnost <xref:System.Activities.Statements.WriteLine> se aktivita "Hello, world".  
  
     Pracovní postup by teď měl vypadat podobně jako v následujícím diagramu.  
  
     ![Jednoduché pracovního postupu](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")  
  
### <a name="create-the-workflow-creation-service-contract"></a>Vytvoření kontraktu služby vytvoření pracovního postupu  
  
1.  Přidat nový projekt knihovny třídy s názvem `Shared` k `CreationEndpointTest` řešení.  
  
2.  Přidat odkaz na System.ServiceModel.dll System.Configuration a System.ServiceModel.Activities k `Shared` projektu.  
  
3.  Přejmenujte soubor Class1.cs IWorkflowCreation.cs a následující kód do souboru.  
  
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
  
     Tento kontrakt definuje dvě operace, jak vytvořit novou instanci pracovního postupu bez služby, kterou jste právě vytvořili. Jeden vytvoří novou instanci s ID generovaného instance a dalších umožňuje zadat ID instance pro nové instance pracovního postupu.  Obě metody umožňují předat parametry do nové instance pracovního postupu. Tento kontrakt budou vystavené <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> tak, aby klienti k vytvoření nové instance pracovního postupu jiné služby.  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a>Odvození třídy z WorkflowHostingEndpoint  
  
1.  Přidejte novou třídu s názvem `CreationEndpoint` odvozené z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> k `Shared` projektu.  
  
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
  
2.  Přidat místní statického <xref:System.Uri> proměnné s názvem `defaultBaseUri` k `CreationEndpoint` třídy.  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  Přidejte následující konstruktor `CreationEndpoint` třídy. Všimněte si určíme `IWorkflowCreation` kontraktu služby ve volání základní konstruktoru.  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  Přidejte následující konstruktor výchozí `CreationEndpoint` třídy.  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  Přidání statického `DefaultBaseUri` vlastnost, která má `CreationEndpoint` třídy. Tato vlastnost slouží k uložení výchozí základní identifikátor URI, pokud není k dispozici.  
  
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
  
6.  Vytvořte následující metodu k získání výchozí vazby má použít pro vytvoření koncového bodu.  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> metoda vrátí ID instance pracovního postupu Pokud `Action` záhlaví končí "Vytvořit" vrátí prázdný identifikátor GUID, pokud `Action` záhlaví končí textem "CreateWithInstanceId" vrátí identifikátor GUID předán do metody. Jinak, throw <xref:System.InvalidOperationException>. Tyto `Action` hlavičky odpovídají těchto dvou operací, které jsou definované v `IWorkflowCreation` kontrakt služby.  
  
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
  
8.  Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> metodu pro vytvoření <xref:System.ServiceModel.Activities.WorkflowCreationContext> a přidat všechny argumenty pro pracovní postup, odeslání instance ID do klienta a pak se vraťte <xref:System.ServiceModel.Activities.WorkflowCreationContext>.  
  
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
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a>Vytvořit element standardní koncový bod a umožní vám nakonfigurovat WorkflowCreationEndpoint  
  
1.  Přidat odkaz na sdílené v `CreationEndpoint` projektu  
  
2.  Přidejte novou třídu s názvem `CreationEndpointElement`, odvozené z <xref:System.ServiceModel.Configuration.StandardEndpointElement> k `CreationEndpoint` projektu. Tato třída bude reprezentovat `CreationEndpoint` v souboru web.config.  
  
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
  
3.  Přidat vlastnost s názvem `EndpointType` k návratový typ koncového bodu.  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  Přepsání <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> metoda a vraťte se a nové `CreationEndpoint`.  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  Přetížení <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>, a <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> metody. Tyto metody právě musí být definované, není nutné přidat žádný kód k nim.  
  
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
  
6.  Přidejte třídu kolekce pro `CreationEndpoint` do souboru CreationEndpointElement.cs v `CreationEndpoint` projektu. Tato třída se používá v konfiguraci k uložení několika `CreationEndpoint` instance v souboru web.config.  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  Sestavte řešení.  
  
### <a name="host-the-workflow-in-iis"></a>Hostitele pracovního postupu ve službě IIS  
  
1.  Vytvořit novou aplikaci s názvem `MyCreationEndpoint` ve službě IIS.  
  
2.  Zkopírujte soubor workflow1.xaml generované návrháře pracovních postupů k adresáři aplikace a přejmenujte jej na workflow1.xamlx.  
  
3.  Kopírovat shared.dll a CreationEndpoint.dll soubory do adresáře bin aplikace (vytvořit adresář bin, pokud není přítomen).  
  
4.  Nahraďte obsah souboru Web.config v `CreationEndpoint` projektu s následujícím kódem.  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  Po `<system.web>` elementu, registrace `CreationEndpoint` přidáním následujícího kódu konfigurace.  
  
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
  
     Takovém postupu zaregistruje `CreationEndpointCollection` třídy, můžete nakonfigurovat `CreationEndpoint` v souboru web.config.  
  
6.  Přidat `<service>` – element (po \</extensions > značka) s `CreationEndpoint` bude naslouchat příchozí zprávy.  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  Přidat \<chování > elementu (po  \< /služby > značka) umožňující metadata služby.  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  Zkopírujte soubor web.config do adresáře aplikace služby IIS.  
  
9. Vyzkoušejte, jestli vytvoření koncového bodu funguje tak, že spuštění aplikace Internet Explorer a procházení k http://localhost/MyCreationEndpoint/Workflow1.xamlx. Internet Explorer musí zobrazí následující obrazovka:  
  
     ![Testování služby](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a>Vytvořte klienta, která bude volat CreationEndpoint.  
  
1.  Přidat novou konzolovou aplikaci do `CreationEndpointTest` řešení.  
  
2.  Přidejte odkazy na System.ServiceModel.dll, System.ServiceModel.Activities a `Shared` projektu.  
  
3.  V `Main` metoda vytvoření <xref:System.ServiceModel.ChannelFactory%601> typu `IWorkflowCreation` a volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Tato možnost vrátí proxy server. Potom můžete volat `Create` na zda proxy serveru k vytvoření instance pracovního postupu hostované v rámci služby IIS:  
  
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
  
4.  Spusťte CreationEndpointClient. Výstup by měl vypadat takto:  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  Neuvidíte výstup pracovního postupu, protože je spuštěna v rámci služby IIS, který nemá žádný výstup konzoly.  
  
## <a name="example"></a>Příklad  
 Následuje kompletní kód této ukázce.  
  
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
  
 V tomto příkladu může zdát matoucí, protože nikdy implementovat služba, která implementuje `IWorkflowCreation`. Důvodem je, že `CreationEndpoint` nemá to pro vás.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hostování v Internetové informační službě](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Doporučené postupy hostování internetové informační služby](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Internetové informace o pokyny k hostování služby](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Architektura pracovního postupu systému Windows](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [Obnovit WorkflowHostingEndpoint záložek](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [Opětovného hostování návrháře pracovních postupů](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Přehled pracovního postupu systému Windows](../../../../docs/framework/windows-workflow-foundation/overview.md)
