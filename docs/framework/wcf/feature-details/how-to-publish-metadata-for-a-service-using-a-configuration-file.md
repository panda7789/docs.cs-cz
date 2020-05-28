---
title: 'Postupy: Publikování metadat služby promocí konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 179ccf97ce4f5e2aa3e132db7e77c93259d5e4ac
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144939"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Postupy: Publikování metadat služby promocí konfiguračního souboru
Jedná se o jedno ze dvou témat s postupy, které ukazují publikování metadat pro službu Windows Communication Foundation (WCF). Existují dva způsoby, jak zadat, jak má služba publikovat metadata, pomocí konfiguračního souboru a pomocí kódu. V tomto tématu se dozvíte, jak publikovat metadata pro službu pomocí konfiguračního souboru.  
  
> [!CAUTION]
> V tomto tématu se dozvíte, jak publikovat metadata nezabezpečeným způsobem. Každý klient může získat metadata ze služby. Pokud vyžadujete, aby služba publikovala metadata zabezpečeným způsobem, přečtěte si téma [Vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v kódu naleznete v tématu [How to: Publish metadata for a Service using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikování metadat umožňuje klientům načíst metadata pomocí žádosti o WS-Transfer GET nebo požadavku HTTP/GET pomocí `?wsdl` řetězce dotazu. Abyste měli jistotu, že kód funguje, vytvořte základní službu WCF. V zájmu jednoduchosti je základní Samoobslužná služba k dispozici v následujícím kódu.  
  
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
  
 Tato služba je Samoobslužná služba, která je nakonfigurovaná pomocí konfiguračního souboru. Následující konfigurační soubor slouží jako výchozí bod.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Publikování metadat služby WCF pomocí konfiguračního souboru aplikace  
  
1. V souboru App. config po zavření `</services>` elementu vytvořte `<behaviors>` element.  

2. V rámci `<behaviors>` elementu přidejte `<serviceBehaviors>` element.  

3. Přidejte `<behavior>` prvek do `<serviceBehaviors>` prvku a zadejte hodnotu `name` atributu `<behavior>` elementu.  

4. Přidejte `<serviceMetadata>` element do `<behavior>` elementu. Nastavte `httpGetEnabled` atribut na `true` a `policyVersion` atribut na Policy15. `httpGetEnabled`umožňuje službě reagovat na požadavky na metadata vytvořené požadavkem HTTP GET. `policyVersion`oznamuje službě, aby při generování metadat dodržovala WS-Policy 1,5.  

5. Přidejte `behaviorConfiguration` atribut do `<service>` elementu a určete `name` atribut `<behavior>` prvku přidaný v kroku 1, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
6. Přidejte jeden nebo více `<endpoint>` elementů s kontraktem nastaveným na `IMetadataExchange` , jak je znázorněno v následujícím příkladu kódu.  
  
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
  
7. U koncových bodů metadat přidaných v předchozím kroku nastavte `binding` atribut na jednu z následujících možností:  
  
    - `mexHttpBinding`pro publikování HTTP.  
  
    - `mexHttpsBinding`pro publikování HTTPS.  
  
    - `mexNamedPipeBinding`pro publikaci pojmenovaného kanálu.  
  
    - `mexTcpBinding`pro publikaci TCP.  
  
8. U koncových bodů metadat přidaných v předchozím kroku nastavte adresu na hodnotu:  
  
    - Prázdný řetězec pro použití základní adresy hostitelské aplikace jako bodu publikace, pokud je základní adresa shodná s vazbou metadat.  
  
    - Relativní adresa, pokud má hostitelská aplikace základní adresu.  
  
    - Absolutní adresa.  
  
9. Vytvořte a spusťte konzolovou aplikaci.  
  
10. Pomocí Internet Exploreru přejděte na základní adresu služby ( `http://localhost:8001/MetadataSample` v této ukázce) a ověřte, jestli je zapnuté publikování metadat. V takovém případě se zobrazí zpráva v horní části výsledné stránky: "publikování metadat pro tuto službu je momentálně zakázané."  
  
### <a name="to-use-default-endpoints"></a>Použití výchozích koncových bodů  
  
1. Chcete-li nakonfigurovat metadata pro službu, která používá výchozí koncové body, zadejte do <xref:System.ServiceModel.Description.ServiceMetadataBehavior> konfiguračního souboru jako v předchozím příkladu, ale nezadávejte žádné koncové body. Konfigurační soubor by pak vypadal takto.  
  
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
  
     Vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> s `httpGetEnabled` nastavenou hodnotou `true` , služba má povolenou metadata publikování a protože nebyly explicitně přidány žádné koncové body, modul runtime přidá výchozí koncové body. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci základní služby WCF a konfiguračního souboru, který publikuje metadata pro službu.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Postupy: Hostování služby WCF ve spravované aplikaci](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Vlastní hostování](../../../../docs/framework/wcf/samples/self-host.md)
- [Přehled architektury metadat](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [Používání metadat](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [Postupy: Publikování metadat služby promocí kódu](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
