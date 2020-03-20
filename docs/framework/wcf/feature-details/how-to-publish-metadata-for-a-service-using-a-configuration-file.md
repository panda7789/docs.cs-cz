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
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a>Postupy: Publikování metadat služby promocí konfiguračního souboru
Toto je jedno ze dvou témat s postupy, které demonstrují publikování metadat pro službu WCF (Windows Communication Foundation). Existují dva způsoby, jak určit, jak by měla služba publikovat metadata pomocí konfiguračního souboru a pomocí kódu. Toto téma ukazuje, jak publikovat metadata pro službu pomocí konfiguračního souboru.  
  
> [!CAUTION]
> Toto téma ukazuje, jak publikovat metadata nezabezpečeným způsobem. Každý klient může načíst metadata ze služby. Pokud požadujete, aby vaše služba publikovala metadata zabezpečeným způsobem, přečtěte si část [Vlastní koncový bod zabezpečených metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).  
  
 Další informace o publikování metadat v kódu naleznete v [tématu How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md). Publikování metadat umožňuje klientům načíst metadata pomocí požadavku WS-Transfer GET `?wsdl` nebo požadavku HTTP/GET pomocí řetězce dotazu. Chcete-li se ujistit, že kód funguje, vytvořte základní službu WCF. Pro jednoduchost je základní samoobslužná služba k dispozici v následujícím kódu.  
  
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
  
 Tato služba je samoobslužná služba, která je konfigurována pomocí konfiguračního souboru. Následující konfigurační soubor slouží jako výchozí bod.  
  
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
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a>Publikování metadat pro službu WCF pomocí konfiguračního souboru aplikace  
  
1. V souboru App.config za `</services>` uzavíracím `<behaviors>` prvkem vytvořte prvek.  

2. V `<behaviors>` rámci prvku `<serviceBehaviors>` přidejte prvek.  

3. Přidejte `<behavior>` prvek `<serviceBehaviors>` do elementu a `name` zadejte `<behavior>` hodnotu atributu prvku.  

4. Přidejte `<serviceMetadata>` prvek `<behavior>` do prvku. Nastavte `httpGetEnabled` atribut `true` a `policyVersion` atribut Policy15. `httpGetEnabled`umožňuje službě reagovat na požadavky metadat provedené požadavkem HTTP GET. `policyVersion`informuje službu, aby při generování metadat odpovídala zásadám WS-Policy 1.5.  

5. Přidejte `behaviorConfiguration` atribut `<service>` do prvku `name` a zadejte atribut `<behavior>` prvku přidaného v kroku 1, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
6. Přidejte jeden `<endpoint>` nebo více prvků `IMetadataExchange`se sadou smlouvy na , jak je znázorněno v následujícím příkladu kódu.  
  
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
  
7. U koncových bodů metadat přidaných v `binding` předchozím kroku nastavte atribut na jednu z následujících možností:  
  
    - `mexHttpBinding`pro publikaci HTTP.  
  
    - `mexHttpsBinding`pro publikaci HTTPS.  
  
    - `mexNamedPipeBinding`pro pojmenovanou publikaci kanálu.  
  
    - `mexTcpBinding`pro publikaci TCP.  
  
8. U koncových bodů metadat přidaných v předchozím kroku nastavte adresu rovnou:  
  
    - Prázdný řetězec pro použití základní adresy hostitelské aplikace jako bodu publikace, pokud je základní adresa stejná jako vazba metadat.  
  
    - Relativní adresa, pokud hostitelská aplikace má základní adresu.  
  
    - Absolutní adresa.  
  
9. Vytvořte a spusťte konzolovou aplikaci.  
  
10. Pomocí aplikace Internet Explorer vyhledejte základníhttp://localhost:8001/MetadataSample adresu služby (v této ukázce) a ověřte, zda je publikování metadat zapnuto. Pokud tomu tak není, zobrazí se v horní části výsledné stránky zpráva: "Publikování metadat pro tuto službu je aktuálně zakázáno."  
  
### <a name="to-use-default-endpoints"></a>Použití výchozích koncových bodů  
  
1. Chcete-li nakonfigurovat metadata ve službě, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> která používá výchozí koncové body, zadejte v konfiguračním souboru jako v předchozím příkladu, ale nezadávejte žádné koncové body. Konfigurační soubor by pak vypadat takto.  
  
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
  
     Vzhledem k <xref:System.ServiceModel.Description.ServiceMetadataBehavior> tomu, `httpGetEnabled` že `true`služba má s nastavenou na , služba má povolené metadata publikování a protože žádné koncové body byly explicitně přidány, modul runtime přidá výchozí koncové body. Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
