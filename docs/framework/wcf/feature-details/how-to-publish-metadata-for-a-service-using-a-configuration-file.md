---
title: 'Postupy: Publikování metadat služby promocí konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 81bf7db9ec25ae112127712dcd0443d3e045bc10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552798"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="011a1-102">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="011a1-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="011a1-103">Toto je jedna z dva postupy: témata, které ukazují publikování metadat služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="011a1-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="011a1-104">Existují dva způsoby, jak určit, jak by měla služba publikování metadat, je používán konfigurační soubor a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="011a1-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="011a1-105">Toto téma ukazuje, jak publikování metadat služby promocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="011a1-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="011a1-106">Toto téma ukazuje, jak měla být zveřejněna metadata nezabezpečené způsobem.</span><span class="sxs-lookup"><span data-stu-id="011a1-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="011a1-107">Jakýkoli klient může načíst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="011a1-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="011a1-108">Pokud budete potřebovat bezpečným způsobem být zveřejněna metadata služby, najdete v článku [vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="011a1-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="011a1-109">Další informace o publikování metadat v kódu, naleznete v tématu [jak: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="011a1-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="011a1-110">Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="011a1-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="011a1-111">Ujistěte se, že kód funguje, vytvořte základní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="011a1-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="011a1-112">Pro jednoduchost základní služby v místním prostředí najdete v následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="011a1-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="011a1-113">Tato služba je služba v místním prostředí, který je nakonfigurovaný pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="011a1-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="011a1-114">Následující konfigurační soubor slouží jako výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="011a1-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="011a1-115">Chcete-li být zveřejněna metadata pro služby WCF pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="011a1-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="011a1-116">V souboru App.config, za uzavírací `</services>` elementu, vytvořit `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="011a1-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="011a1-117">V rámci `<behaviors>` elementu, přidejte `<serviceBehaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="011a1-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="011a1-118">Přidat `<behavior>` elementu `<serviceBehaviors>` element a zadat hodnotu `name` atribut `<behavior>` element.</span><span class="sxs-lookup"><span data-stu-id="011a1-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="011a1-119">Přidat `<serviceMetadata>` elementu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="011a1-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="011a1-120">Nastavte `httpGetEnabled` atribut `true` a `policyVersion` atribut Policy15.</span><span class="sxs-lookup"><span data-stu-id="011a1-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="011a1-121">`httpGetEnabled` umožňuje službě reagovat na požadavky metadat provedené požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="011a1-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="011a1-122">`policyVersion` říká službě a při generování metadat v souladu s 1.5 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="011a1-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="011a1-123">Přidat `behaviorConfiguration` atribut `<service>` elementu a zadejte `name` atribut `<behavior>` element přidali v kroku 1, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="011a1-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6.  <span data-ttu-id="011a1-124">Přidejte jeden nebo více `<endpoint>` prvky s kontraktem nastavena na `IMetadataExchange`, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="011a1-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7.  <span data-ttu-id="011a1-125">Pro koncové body metadat přidali v předchozím kroku, nastavte `binding` atribut na jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="011a1-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="011a1-126">`mexHttpBinding` pro publikaci HTTP.</span><span class="sxs-lookup"><span data-stu-id="011a1-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="011a1-127">`mexHttpsBinding` pro publikaci HTTPS.</span><span class="sxs-lookup"><span data-stu-id="011a1-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="011a1-128">`mexNamedPipeBinding` pro publikaci pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="011a1-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="011a1-129">`mexTcpBinding` pro publikaci TCP.</span><span class="sxs-lookup"><span data-stu-id="011a1-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="011a1-130">Pro koncové body metadat přidali v předchozím kroku nastavte adresu na:</span><span class="sxs-lookup"><span data-stu-id="011a1-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="011a1-131">Prázdný řetězec pro použití základní adresa hostitelské aplikace jako bod publikace, pokud základní adresa je stejný jako vazby metadat.</span><span class="sxs-lookup"><span data-stu-id="011a1-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="011a1-132">Relativní adresa, pokud má základní adresa hostitele aplikace.</span><span class="sxs-lookup"><span data-stu-id="011a1-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="011a1-133">Absolutní adresu.</span><span class="sxs-lookup"><span data-stu-id="011a1-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="011a1-134">Vytvořte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="011a1-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="011a1-135">Pomocí aplikace Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, zda je povoleno publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="011a1-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="011a1-136">Pokud ne, zobrazí se zpráva v horní části výslednou stránku: "Publikování metadat pro tuto službu je aktuálně zakázaný."</span><span class="sxs-lookup"><span data-stu-id="011a1-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="011a1-137">Chcete-li použít výchozí koncové body</span><span class="sxs-lookup"><span data-stu-id="011a1-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="011a1-138">Konfigurace pro službu, která používá výchozí koncové body metadat, zadejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguraci soubor jako v předchozím příkladu, ale nezadávejte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="011a1-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="011a1-139">Konfigurační soubor by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="011a1-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="011a1-140">Vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> s `httpGetEnabled` nastavena na `true`má povoleno publikování metadat služby a protože žádné koncové body byly explicitně přidány, modulu runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="011a1-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="011a1-141">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="011a1-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="011a1-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="011a1-142">Example</span></span>  
 <span data-ttu-id="011a1-143">Následující příklad kódu ukazuje implementaci základní služby WCF a konfigurační soubor, který publikuje metadat služby.</span><span class="sxs-lookup"><span data-stu-id="011a1-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="011a1-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="011a1-144">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="011a1-145">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="011a1-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="011a1-146">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="011a1-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="011a1-147">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="011a1-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="011a1-148">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="011a1-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="011a1-149">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="011a1-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
