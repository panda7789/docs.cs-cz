---
title: 'Postupy: Publikování metadat služby promocí konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 367ebeee5c12d809a758f1bee73dfaadda85788d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295533"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Postupy: Publikování metadat služby promocí konfiguračního souboru
Toto je jedna z dva postupy: témata, které ukazují publikování metadat služby Windows Communication Foundation (WCF). Existují dva způsoby, jak určit, jak by měla služba publikování metadat, je používán konfigurační soubor a pomocí kódu. Toto téma ukazuje, jak publikování metadat služby promocí konfiguračního souboru.  
  
> [!CAUTION]
>  Toto téma ukazuje, jak měla být zveřejněna metadata nezabezpečené způsobem. Jakýkoli klient může načíst metadata ze služby. Pokud budete potřebovat bezpečným způsobem být zveřejněna metadata služby, najdete v článku [vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v kódu, naleznete v tématu [jak: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu. Ujistěte se, že kód funguje, vytvořte základní služby WCF. Pro jednoduchost základní služby v místním prostředí najdete v následujícím kódem.  
  
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
  
 Tato služba je služba v místním prostředí, který je nakonfigurovaný pomocí konfiguračního souboru. Následující konfigurační soubor slouží jako výchozí bod.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Chcete-li být zveřejněna metadata pro služby WCF pomocí konfiguračního souboru aplikace  
  
1. V souboru App.config, za uzavírací `</services>` elementu, vytvořit `<behaviors>` elementu.  

2. V rámci `<behaviors>` elementu, přidejte `<serviceBehaviors>` elementu.  

3. Přidat `<behavior>` elementu `<serviceBehaviors>` element a zadat hodnotu `name` atribut `<behavior>` element.  

4. Přidat `<serviceMetadata>` elementu `<behavior>` elementu. Nastavte `httpGetEnabled` atribut `true` a `policyVersion` atribut Policy15. `httpGetEnabled` umožňuje službě reagovat na požadavky metadat provedené požadavek HTTP GET. `policyVersion` říká službě a při generování metadat v souladu s 1.5 WS-Policy.  

5. Přidat `behaviorConfiguration` atribut `<service>` elementu a zadejte `name` atribut `<behavior>` element přidali v kroku 1, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
6. Přidejte jeden nebo více `<endpoint>` prvky s kontraktem nastavena na `IMetadataExchange`, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
7. Pro koncové body metadat přidali v předchozím kroku, nastavte `binding` atribut na jednu z následujících akcí:  
  
    -   `mexHttpBinding` pro publikaci HTTP.  
  
    -   `mexHttpsBinding` pro publikaci HTTPS.  
  
    -   `mexNamedPipeBinding` pro publikaci pojmenovaného kanálu.  
  
    -   `mexTcpBinding` pro publikaci TCP.  
  
8. Pro koncové body metadat přidali v předchozím kroku nastavte adresu na:  
  
    -   Prázdný řetězec pro použití základní adresa hostitelské aplikace jako bod publikace, pokud základní adresa je stejný jako vazby metadat.  
  
    -   Relativní adresa, pokud má základní adresa hostitele aplikace.  
  
    -   Absolutní adresu.  
  
9. Vytvořte a spusťte konzolovou aplikaci.  
  
10. Pomocí aplikace Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, zda je povoleno publikování metadat. Pokud ne, zobrazí se zpráva v horní části výslednou stránku: "Publikování metadat pro tuto službu je aktuálně zakázaný."  
  
### <a name="to-use-default-endpoints"></a>Chcete-li použít výchozí koncové body  
  
1. Konfigurace pro službu, která používá výchozí koncové body metadat, zadejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> v konfiguraci soubor jako v předchozím příkladu, ale nezadávejte žádné koncové body. Konfigurační soubor by měl vypadat takto.  
  
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
  
     Vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> s `httpGetEnabled` nastavena na `true`má povoleno publikování metadat služby a protože žádné koncové body byly explicitně přidány, modulu runtime přidá výchozí koncové body. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci základní služby WCF a konfigurační soubor, který publikuje metadat služby.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Vlastní hostování](../../../../docs/framework/wcf/samples/self-host.md)
- [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
