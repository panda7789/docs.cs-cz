---
title: Konfigurace služeb WCF v kódu
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174807"
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu
Windows Communication Foundation (WCF) umožňuje vývojářům konfigurovat služby pomocí konfiguračních souborů nebo kódu.  Konfigurační soubory jsou užitečné, když služba musí být nakonfigurována po nasazení. Při použití konfiguračních souborů potřebuje odborník v IT pouze aktualizovat konfigurační soubor, není vyžadována žádná rekompilace. Konfigurační soubory však může být složité a obtížné udržovat. Neexistuje žádná podpora pro ladění konfiguračních souborů a konfigurační prvky jsou odkazovány názvy, které činí vytváření konfiguračních souborů náchylné k chybám a obtížné. WCF také umožňuje konfigurovat služby v kódu. V dřívějších verzích WCF (4.0 a starší) konfigurace služeb v kódu <xref:System.ServiceModel.ServiceHost> bylo snadné v samoobslužných scénářích, třída vám umožnila konfigurovat koncové body a chování před voláním ServiceHost.Open. Ve scénářích hostovaných na webu však nemáte <xref:System.ServiceModel.ServiceHost> přímý přístup ke třídě. Chcete-li nakonfigurovat webovou hostovanou `System.ServiceModel.ServiceHostFactory` službu, museli jste vytvořit a který vytvořil a provedl potřebnou <xref:System.ServiceModel.Activation.ServiceHostFactory> konfiguraci. Počínaje rozhraním .NET 4.5 poskytuje wcf jednodušší způsob konfigurace samoobslužných i webových hostovaných služeb v kódu.  
  
## <a name="the-configure-method"></a>Metoda Configure  
 Jednoduše definujte veřejnou `Configure` statickou metodu volanou s následujícím podpisem ve třídě implementace služby:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure Metoda trvá <xref:System.ServiceModel.ServiceConfiguration> instance, která umožňuje vývojáři přidat koncové body a chování. Tato metoda je volána WCF před otevřením hostitele služby. Pokud je definována, budou všechna nastavení konfigurace služby zadaná v souboru app.config nebo web.config ignorována.  
  
 Následující fragment kódu ukazuje, jak definovat `Configure` metodu a přidat koncový bod služby, chování koncového bodu a chování služby:  
  
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
  
 Chcete-li povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol, nebo můžete automaticky přidat koncové body voláním ServiceConfiguration.EnableProtocol(Binding), který přidá koncový bod pro každou základní adresu kompatibilní s protokolem a každou definovanou smlouvou o poskytování služeb. Následující kód ukazuje, jak používat metodu ServiceConfiguration.EnableProtocol:  
  
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
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 Nastavení v části `protocolMappings` <> se používají pouze v případě, že žádné koncové body aplikace jsou přidány do <xref:System.ServiceModel.ServiceConfiguration> programově. Volitelně můžete načíst konfiguraci služby z <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> výchozího konfiguračního souboru aplikace voláním a následným změnou nastavení. Třída <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> také umožňuje načíst konfiguraci z centralizované konfigurace. Následující kód ukazuje, jak implementovat toto:  
  
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
> Všimněte <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> si, `host` že ignoruje `service` nastavení> `system.serviceModel` <v rámci <> značky <>. Koncepčně `host` <> je o konfiguraci hostitele, nikoli o konfiguraci služby, a načte se před spuštěním metody Configure.  
  
## <a name="see-also"></a>Viz také

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
