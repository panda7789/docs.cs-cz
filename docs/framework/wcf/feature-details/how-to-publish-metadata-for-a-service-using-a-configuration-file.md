---
title: 'Postupy: Publikování metadat služby promocí konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 7ea0a2aa386f747b89f56f21d75a97e4409140a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184873"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="0b079-102">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0b079-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="0b079-103">Toto je jedno ze dvou témat s postupy, které demonstrují publikování metadat pro službu WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="0b079-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0b079-104">Existují dva způsoby, jak určit, jak by měla služba publikovat metadata pomocí konfiguračního souboru a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="0b079-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="0b079-105">Toto téma ukazuje, jak publikovat metadata pro službu pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0b079-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0b079-106">Toto téma ukazuje, jak publikovat metadata nezabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="0b079-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="0b079-107">Každý klient může načíst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="0b079-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="0b079-108">Pokud požadujete, aby vaše služba publikovala metadata zabezpečeným způsobem, přečtěte si část [Vlastní koncový bod zabezpečených metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="0b079-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="0b079-109">Další informace o publikování metadat v kódu naleznete v [tématu How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="0b079-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="0b079-110">Publikování metadat umožňuje klientům načíst metadata pomocí požadavku WS-Transfer GET `?wsdl` nebo požadavku HTTP/GET pomocí řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="0b079-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="0b079-111">Chcete-li se ujistit, že kód funguje, vytvořte základní službu WCF.</span><span class="sxs-lookup"><span data-stu-id="0b079-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="0b079-112">Pro jednoduchost je základní samoobslužná služba k dispozici v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0b079-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
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
  
 <span data-ttu-id="0b079-113">Tato služba je samoobslužná služba, která je konfigurována pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="0b079-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="0b079-114">Následující konfigurační soubor slouží jako výchozí bod.</span><span class="sxs-lookup"><span data-stu-id="0b079-114">The following configuration file serves as a starting point.</span></span>  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="0b079-115">Publikování metadat pro službu WCF pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="0b079-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="0b079-116">V souboru App.config za `</services>` uzavíracím `<behaviors>` prvkem vytvořte prvek.</span><span class="sxs-lookup"><span data-stu-id="0b079-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="0b079-117">V `<behaviors>` rámci prvku `<serviceBehaviors>` přidejte prvek.</span><span class="sxs-lookup"><span data-stu-id="0b079-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="0b079-118">Přidejte `<behavior>` prvek `<serviceBehaviors>` do elementu a `name` zadejte `<behavior>` hodnotu atributu prvku.</span><span class="sxs-lookup"><span data-stu-id="0b079-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="0b079-119">Přidejte `<serviceMetadata>` prvek `<behavior>` do prvku.</span><span class="sxs-lookup"><span data-stu-id="0b079-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="0b079-120">Nastavte `httpGetEnabled` atribut `true` a `policyVersion` atribut Policy15.</span><span class="sxs-lookup"><span data-stu-id="0b079-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="0b079-121">`httpGetEnabled`umožňuje službě reagovat na požadavky metadat provedené požadavkem HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="0b079-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="0b079-122">`policyVersion`informuje službu, aby při generování metadat odpovídala zásadám WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="0b079-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="0b079-123">Přidejte `behaviorConfiguration` atribut `<service>` do prvku `name` a zadejte atribut `<behavior>` prvku přidaného v kroku 1, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0b079-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
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
  
6. <span data-ttu-id="0b079-124">Přidejte jeden `<endpoint>` nebo více prvků `IMetadataExchange`se sadou smlouvy na , jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="0b079-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
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
  
7. <span data-ttu-id="0b079-125">U koncových bodů metadat přidaných v `binding` předchozím kroku nastavte atribut na jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="0b079-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="0b079-126">`mexHttpBinding`pro publikaci HTTP.</span><span class="sxs-lookup"><span data-stu-id="0b079-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="0b079-127">`mexHttpsBinding`pro publikaci HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0b079-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="0b079-128">`mexNamedPipeBinding`pro pojmenovanou publikaci kanálu.</span><span class="sxs-lookup"><span data-stu-id="0b079-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="0b079-129">`mexTcpBinding`pro publikaci TCP.</span><span class="sxs-lookup"><span data-stu-id="0b079-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="0b079-130">U koncových bodů metadat přidaných v předchozím kroku nastavte adresu rovnou:</span><span class="sxs-lookup"><span data-stu-id="0b079-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="0b079-131">Prázdný řetězec pro použití základní adresy hostitelské aplikace jako bodu publikace, pokud je základní adresa stejná jako vazba metadat.</span><span class="sxs-lookup"><span data-stu-id="0b079-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="0b079-132">Relativní adresa, pokud hostitelská aplikace má základní adresu.</span><span class="sxs-lookup"><span data-stu-id="0b079-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="0b079-133">Absolutní adresa.</span><span class="sxs-lookup"><span data-stu-id="0b079-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="0b079-134">Vytvořte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0b079-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="0b079-135">Pomocí aplikace Internet Explorer vyhledejte základníhttp://localhost:8001/MetadataSample adresu služby (v této ukázce) a ověřte, zda je publikování metadat zapnuto.</span><span class="sxs-lookup"><span data-stu-id="0b079-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="0b079-136">Pokud tomu tak není, zobrazí se v horní části výsledné stránky zpráva: "Publikování metadat pro tuto službu je aktuálně zakázáno."</span><span class="sxs-lookup"><span data-stu-id="0b079-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="0b079-137">Použití výchozích koncových bodů</span><span class="sxs-lookup"><span data-stu-id="0b079-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="0b079-138">Chcete-li nakonfigurovat metadata ve službě, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> která používá výchozí koncové body, zadejte v konfiguračním souboru jako v předchozím příkladu, ale nezadávejte žádné koncové body.</span><span class="sxs-lookup"><span data-stu-id="0b079-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="0b079-139">Konfigurační soubor by pak vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="0b079-139">The configuration file would then look like this.</span></span>  
  
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
  
     <span data-ttu-id="0b079-140">Vzhledem k <xref:System.ServiceModel.Description.ServiceMetadataBehavior> tomu, `httpGetEnabled` že `true`služba má s nastavenou na , služba má povolené metadata publikování a protože žádné koncové body byly explicitně přidány, modul runtime přidá výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="0b079-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="0b079-141">Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b079-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b079-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b079-142">Example</span></span>  
 <span data-ttu-id="0b079-143">Následující příklad kódu ukazuje implementaci základní služby WCF a konfiguračního souboru, který publikuje metadata pro službu.</span><span class="sxs-lookup"><span data-stu-id="0b079-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b079-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b079-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="0b079-145">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="0b079-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="0b079-146">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="0b079-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="0b079-147">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="0b079-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="0b079-148">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="0b079-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="0b079-149">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="0b079-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
