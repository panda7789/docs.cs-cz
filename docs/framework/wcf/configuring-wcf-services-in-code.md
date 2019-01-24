---
title: Konfigurace služeb WCF v kódu
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: d55c4994dfa322619f7e5e5911c23d68b439646a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718764"
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu
Windows Communication Foundation (WCF) umožňuje vývojářům konfigurovat služeb pomocí konfiguračních souborů nebo kódu.  Konfigurační soubory jsou užitečné, pokud je potřeba nakonfigurovat po nasazení služby. Při použití konfiguračních souborů, odborníci na IT jenom je potřeba aktualizovat konfigurační soubor, žádné rekompilace je povinný. Konfigurační soubory, ale lze komplexní a obtížné na správu. Neexistuje žádná podpora pro ladění konfigurační soubory a konfigurační prvky, které je odkazováno dle názvy, které umožňuje vytváření konfigurační soubory obtížné a náchylné k chybě. WCF můžete také nakonfigurovat v kódu. V dřívějších verzích konfigurace služby WCF (4.0 a starší) v kódu bylo snadné v místním prostředí scénáře <xref:System.ServiceModel.ServiceHost> třída je možné nakonfigurovat koncové body a chování před voláním ServiceHost.Open povolená. Ve scénářích hostovaná na webu, ale nemáte přímý přístup k <xref:System.ServiceModel.ServiceHost> třídy. Konfigurace webového hostovaná služba byla potřeba k vytvoření `System.ServiceModel.ServiceHostFactory` vytvořený <xref:System.ServiceModel.Activation.ServiceHostFactory> a provedení všech potřebných konfigurace. Počínaje .NET 4.5 WCF poskytuje snadný způsob, jak nakonfigurovat i v místním prostředí a web hostované služby v kódu.  
  
## <a name="the-configure-method"></a>Metoda Configure  
 Jednoduše definovat veřejné statické metody volá `Configure` s následující signaturou ve své třídě implementace služby:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Konfigurovat metoda přijímá <xref:System.ServiceModel.ServiceConfiguration> instanci, která umožňuje vývojářům přidat koncové body a chování. Tato metoda je volána službou WCF před otevřením hostitele služby. Při definování, ignorují se jakékoli nastavení konfigurace služby zadaný v souboru app.config nebo web.config.  
  
 Následující fragment kódu ukazuje, jak definovat `Configure` metoda a přidat koncový bod služby, chování koncového bodu a chování služby:  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 Pokud chcete povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol nebo můžete automaticky přidat koncové body voláním ServiceConfiguration.EnableProtocol(Binding), který přidá koncový bod pro každou základní adresu kompatibilní s protokolem a každá služba kontrakt definovaný. Následující kód ukazuje, jak použít metodu ServiceConfiguration.EnableProtocol:  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 Nastavení <`protocolMappings`> části se použijí pouze, pokud žádné koncové body aplikace se přidají do <xref:System.ServiceModel.ServiceConfiguration> prostřednictvím kódu programu. Volitelně můžete načíst konfiguraci služby z konfiguračního souboru aplikace výchozí voláním <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a pak změňte nastavení. <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Tříd také umožňuje načtení konfigurace z centralizovaného konfigurace. Následující kód ukazuje, jak implementovat toto:  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
>  Všimněte si, že <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Nastavení v rámci <`service`> značky <`system.serviceModel`>. Koncepčně <`host`> je o konfiguraci hostitele, není konfigurace služby a it získá načtené před provedením metody konfigurace.  
  
## <a name="see-also"></a>Viz také:
- [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Konfigurace chování klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)
- [Konfigurace](../../../docs/framework/wcf/samples/configuration-sample.md)
- [Aktivace založená na konfiguraci v IIS a WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [Konfigurace a podpora metadat](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [Konfigurace](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [Postupy: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Postupy: Zadání klientské vazby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
