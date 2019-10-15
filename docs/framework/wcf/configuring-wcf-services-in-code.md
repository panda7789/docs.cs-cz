---
title: Konfigurace služeb WCF v kódu
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: c6bcf08511470d28e1087108d95e477683b0338b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320634"
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu
Windows Communication Foundation (WCF) umožňuje vývojářům nakonfigurovat služby pomocí konfiguračních souborů nebo kódu.  Konfigurační soubory jsou užitečné, když po nasazení potřebujete nakonfigurovat službu. Při použití konfiguračních souborů potřebuje IT specialista aktualizovat pouze konfigurační soubor, není nutné znovu zkompilována. Konfigurační soubory ale mohou být složité a obtížné udržovat. Neexistuje žádná podpora pro ladění konfiguračních souborů a konfigurační prvky jsou odkazovány pomocí názvů, které usnadňují a obtíže při vytváření konfiguračních souborů. WCF také umožňuje nakonfigurovat služby v kódu. V dřívějších verzích WCF (4,0 a starší) konfigurace služeb v kódu byla v rámci scénářů s vlastním hostováním velmi snadná, třída <xref:System.ServiceModel.ServiceHost> umožňuje nakonfigurovat koncové body a chování před voláním třídy ServiceHost. Open. Ve scénářích, kde se nachází web, ale nemáte přímý přístup ke třídě <xref:System.ServiceModel.ServiceHost>. Pro konfiguraci webové hostované služby jste museli vytvořit `System.ServiceModel.ServiceHostFactory`, která vytvořila <xref:System.ServiceModel.Activation.ServiceHostFactory> a provedla jakoukoli potřebnou konfiguraci. Počínaje verzí .NET 4,5 nabízí WCF snazší způsob, jak v kódu nakonfigurovat služby hostované v místním prostředí i na webu.  
  
## <a name="the-configure-method"></a>Metoda Configure  
 Jednoduše definujte veřejnou statickou metodu s názvem `Configure` s následující signaturou ve třídě implementace služby:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Metoda Configure přebírá instanci <xref:System.ServiceModel.ServiceConfiguration>, která vývojářům umožňuje přidat koncové body a chování. Tato metoda je volána službou WCF před otevřením hostitele služby. Při definování budou všechna nastavení konfigurace služby zadaná v souboru App. config nebo Web. config ignorována.  
  
 Následující fragment kódu ukazuje, jak definovat metodu `Configure` a přidat koncový bod služby, chování koncového bodu a chování služby:  
  
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
  
 Pokud chcete povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol, nebo můžete automaticky přidat koncové body voláním ServiceConfiguration. EnableProtocol (Binding), který přidá koncový bod pro každou základní adresu. kompatibilní s protokolem a všemi definovanými kontrakty služby. Následující kód ilustruje, jak použít metodu ServiceConfiguration. EnableProtocol:  
  
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
  
 Nastavení v části < `protocolMappings` > se použijí jenom v případě, že se do <xref:System.ServiceModel.ServiceConfiguration> nepřidaly žádné koncové body aplikace. Můžete volitelně načíst konfiguraci služby z výchozího konfiguračního souboru aplikace voláním <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a potom změnit nastavení. Třída <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> také umožňuje načíst konfiguraci z centralizované konfigurace. Následující kód ilustruje, jak implementovat toto:  
  
```csharp
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
> Všimněte si, že hodnota <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje nastavení > < `service` > < `system.serviceModel` > < `host`. Koncepční < `host` > se týkají konfigurace hostitele, nikoli konfigurace služby a načítá se před spuštěním metody konfigurace.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace služeb pomocí konfiguračních souborů](configuring-services-using-configuration-files.md)
- [Konfigurace chování klienta](configuring-client-behaviors.md)
- [Zjednodušená konfigurace](simplified-configuration.md)
- [Konfigurace](./samples/configuration-sample.md)
- [Aktivace založená na konfiguraci v IIS a WAS](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [Konfigurace a podpora metadat](./extending/configuration-and-metadata-support.md)
- [Konfigurace](./diagnostics/exceptions-reference/configuration.md)
- [Postupy: Určení vazby služby v konfiguraci](how-to-specify-a-service-binding-in-configuration.md)
- [Postupy: Vytvoření koncového bodu služby v konfiguraci](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Postupy: Publikování metadat služby promocí konfiguračního souboru](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Postupy: Určení vazby klienta v konfiguraci](how-to-specify-a-client-binding-in-configuration.md)
