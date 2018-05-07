---
title: Konfigurace služeb WCF v kódu
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 2046ee00bef0f3e84a61151474c777d64005a30c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-wcf-services-in-code"></a>Konfigurace služeb WCF v kódu
Windows Communication Foundation (WCF) umožňuje vývojářům konfigurovat služeb pomocí konfiguračních souborů nebo kódu.  Konfigurační soubory jsou užitečné, když je potřeba nakonfigurovat po nasazení služby. Při použití konfigurační soubory, odborník v oblasti IT pouze musí aktualizovat konfigurační soubor, není třeba žádné opětovnou kompilaci. Konfigurační soubory, však může být složité a obtížné. Neexistuje žádná podpora pro ladění konfigurační soubory a konfigurace – elementy odkazují názvy, které umožňuje vytváření konfigurační soubory k chybám a obtížná. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] také umožňuje konfigurovat služby v kódu. V dřívějších verzích [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 a starší) konfigurace služby v kódu se snadno ve vlastním hostováním scénářů <xref:System.ServiceModel.ServiceHost> třída povolena, můžete nakonfigurovat koncové body a chování před volání ServiceHost.Open. Ve scénářích hostovaná na webu, ale nemáte přímý přístup k <xref:System.ServiceModel.ServiceHost> třídy. Konfigurace webové hostované služby, bylo potřeba vytvořit `System.ServiceModel.ServiceHostFactory` vytvořené <xref:System.ServiceModel.Activation.ServiceHostFactory> a provést všechny potřebné konfigurace. Od verze rozhraní .NET 4.5, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] poskytuje snadný způsob, jak nakonfigurovat i samoobslužně hostované a webové hostované služby v kódu.  
  
## <a name="the-configure-method"></a>Metoda konfigurace  
 Jednoduše zadejte veřejnou statickou metodu s názvem `Configure` následující podpisem v třídě implementace služby:  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Provede metodu konfigurace <xref:System.ServiceModel.ServiceConfiguration> instanci, která umožňuje vývojáři přidat koncové body a chování. Tato metoda je volána [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] před otevřením hostitele služby. Pokud je definována, nastavení konfigurace služby, který je zadaný v souboru app.config nebo web.config, bude ignorována.  
  
 Následující fragment kódu ukazuje, jak definovat `Configure` metoda a přidání koncového bodu služby, chování koncového bodu a chování služby:  
  
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
            return string.Format("You entered: {0}", value);  
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
  
 Pokud chcete povolit protokol, jako je například https pro službu, můžete buď explicitně přidat koncový bod, který používá protokol nebo můžete automaticky přidat koncové body voláním ServiceConfiguration.EnableProtocol(Binding), který přidá koncový bod pro každou základní adresu kompatibilní s protokolem a každý kontrakt služby definované. Následující kód ukazuje, jak lze pomocí této metody ServiceConfiguration.EnableProtocol:  
  
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
  
 Nastavení v <`protocolMappings`> části jsou použít jen v případě žádné koncové body aplikace jsou přidány do <xref:System.ServiceModel.ServiceConfiguration> prostřednictvím kódu programu. Volitelně můžete načíst konfiguraci služby z konfiguračního souboru aplikace výchozí voláním <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> a poté změňte nastavení. <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Třída taky umožňuje načíst konfiguraci z centralizované konfigurace. Následující kód ukazuje, jak implementovat toto:  
  
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
>  Všimněte si, že <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignoruje <`host`> Nastavení v rámci <`service`> značky <`system.serviceModel`>. Koncepčně <`host`> je o konfigurace hostitele, není konfigurace služby a získá načíst před spuštěním metody konfigurace.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace služeb pomocí konfiguračních souborů](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Konfigurace chování klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)  
 [Aktivace na základě konfigurace](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [Konfigurace](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [Aktivace založená na konfiguraci v IIS a WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [Konfigurace a podpora metadat](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [Konfigurace](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [Postupy: Určení vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Postupy: Vytvoření koncového bodu služby v konfiguraci](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [Postupy: Publikování metadat služby promocí konfiguračního souboru](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [Postupy: Určení vazby klienta v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
