---
title: 'Postupy: Publikování metadat služby promocí konfiguračního souboru'
description: Naučte se publikovat metadata pro službu WCF pomocí konfiguračního souboru. Publikování umožňuje klientům získat tato metadata pomocí žádosti GET nebo HTTP/GET.
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: d5d425be7f02a204476c4f6e81441aca9ea39fcc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246815"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="683d3-104">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="683d3-104">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="683d3-105">Jedná se o jedno ze dvou témat s postupy, které ukazují publikování metadat pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="683d3-105">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="683d3-106">Existují dva způsoby, jak zadat, jak má služba publikovat metadata, pomocí konfiguračního souboru a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="683d3-106">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="683d3-107">V tomto tématu se dozvíte, jak publikovat metadata pro službu pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="683d3-107">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="683d3-108">V tomto tématu se dozvíte, jak publikovat metadata nezabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="683d3-108">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="683d3-109">Každý klient může získat metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="683d3-109">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="683d3-110">Pokud vyžadujete, aby služba publikovala metadata zabezpečeným způsobem, přečtěte si téma [Vlastní zabezpečený koncový bod metadat](../samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="683d3-110">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="683d3-111">Další informace o publikování metadat v kódu naleznete v tématu [How to: Publish metadata for a Service using Code](how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="683d3-111">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="683d3-112">Publikování metadat umožňuje klientům načíst metadata pomocí žádosti o WS-Transfer GET nebo požadavku HTTP/GET pomocí `?wsdl` řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="683d3-112">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="683d3-113">Abyste měli jistotu, že kód funguje, vytvořte základní službu WCF.</span><span class="sxs-lookup"><span data-stu-id="683d3-113">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="683d3-114">V zájmu jednoduchosti je základní Samoobslužná služba k dispozici v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="683d3-114">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="683d3-115">Tato služba je Samoobslužná služba, která je nakonfigurovaná pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="683d3-115">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="683d3-116">Následující konfigurační soubor slouží jako výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="683d3-116">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="683d3-117">Publikování metadat služby WCF pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="683d3-117">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="683d3-118">V souboru App.config za uzavíracím `</services>` prvkem vytvořte `<behaviors>` element.</span><span class="sxs-lookup"><span data-stu-id="683d3-118">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="683d3-119">V rámci `<behaviors>` elementu přidejte `<serviceBehaviors>` element.</span><span class="sxs-lookup"><span data-stu-id="683d3-119">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="683d3-120">Přidejte `<behavior>` prvek do `<serviceBehaviors>` prvku a zadejte hodnotu `name` atributu `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="683d3-120">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="683d3-121">Přidejte `<serviceMetadata>` element do `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="683d3-121">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="683d3-122">Nastavte `httpGetEnabled` atribut na `true` a `policyVersion` atribut na Policy15.</span><span class="sxs-lookup"><span data-stu-id="683d3-122">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="683d3-123">`httpGetEnabled`umožňuje službě reagovat na požadavky na metadata vytvořené požadavkem HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="683d3-123">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="683d3-124">`policyVersion`oznamuje službě, aby při generování metadat dodržovala WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="683d3-124">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="683d3-125">Přidejte `behaviorConfiguration` atribut do `<service>` elementu a určete `name` atribut `<behavior>` prvku přidaný v kroku 1, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="683d3-125">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6. <span data-ttu-id="683d3-126">Přidejte jeden nebo více `<endpoint>` elementů s kontraktem nastaveným na `IMetadataExchange` , jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="683d3-126">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7. <span data-ttu-id="683d3-127">U koncových bodů metadat přidaných v předchozím kroku nastavte `binding` atribut na jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="683d3-127">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="683d3-128">`mexHttpBinding`pro publikování HTTP.</span><span class="sxs-lookup"><span data-stu-id="683d3-128">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="683d3-129">`mexHttpsBinding`pro publikování HTTPS.</span><span class="sxs-lookup"><span data-stu-id="683d3-129">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="683d3-130">`mexNamedPipeBinding`pro publikaci pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="683d3-130">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="683d3-131">`mexTcpBinding`pro publikaci TCP.</span><span class="sxs-lookup"><span data-stu-id="683d3-131">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="683d3-132">U koncových bodů metadat přidaných v předchozím kroku nastavte adresu na hodnotu:</span><span class="sxs-lookup"><span data-stu-id="683d3-132">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="683d3-133">Prázdný řetězec pro použití základní adresy hostitelské aplikace jako bodu publikace, pokud je základní adresa shodná s vazbou metadat.</span><span class="sxs-lookup"><span data-stu-id="683d3-133">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="683d3-134">Relativní adresa, pokud má hostitelská aplikace základní adresu.</span><span class="sxs-lookup"><span data-stu-id="683d3-134">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="683d3-135">Absolutní adresa.</span><span class="sxs-lookup"><span data-stu-id="683d3-135">An absolute address.</span></span>  
  
9. <span data-ttu-id="683d3-136">Vytvořte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="683d3-136">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="683d3-137">Pomocí Internet Exploreru přejděte na základní adresu služby ( `http://localhost:8001/MetadataSample` v této ukázce) a ověřte, jestli je zapnuté publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="683d3-137">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="683d3-138">V takovém případě se zobrazí zpráva v horní části výsledné stránky: "publikování metadat pro tuto službu je momentálně zakázané."</span><span class="sxs-lookup"><span data-stu-id="683d3-138">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="683d3-139">Použití výchozích koncových bodů</span><span class="sxs-lookup"><span data-stu-id="683d3-139">To use default endpoints</span></span>  
  
1. <span data-ttu-id="683d3-140">Chcete-li nakonfigurovat metadata pro službu, která používá výchozí koncové body, zadejte do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> konfiguračního souboru jako v předchozím příkladu, ale nezadávejte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="683d3-140">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="683d3-141">Konfigurační soubor by pak vypadal takto.</span><span class="sxs-lookup"><span data-stu-id="683d3-141">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="683d3-142">Vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> s `httpGetEnabled` nastavenou hodnotou `true` , služba má povolenou metadata publikování a protože nebyly explicitně přidány žádné koncové body, modul runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="683d3-142">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="683d3-143">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="683d3-143">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="683d3-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="683d3-144">Example</span></span>  
 <span data-ttu-id="683d3-145">Následující příklad kódu ukazuje implementaci základní služby WCF a konfiguračního souboru, který publikuje metadata pro službu.</span><span class="sxs-lookup"><span data-stu-id="683d3-145">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="683d3-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="683d3-146">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="683d3-147">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="683d3-147">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="683d3-148">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="683d3-148">Self-Host</span></span>](../samples/self-host.md)
- [<span data-ttu-id="683d3-149">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="683d3-149">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="683d3-150">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="683d3-150">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="683d3-151">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="683d3-151">How to: Publish Metadata for a Service Using Code</span></span>](how-to-publish-metadata-for-a-service-using-code.md)
