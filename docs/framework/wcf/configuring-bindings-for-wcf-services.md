---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: b91c8ff5a78ef2b2b2db5ea26ae7a1733a97ffd0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurace vazeb pro služby Windows Communication Foundation
Při vytváření aplikace, budete chtít často odložení rozhodnutí, která správci po nasazení aplikace. Například je často žádný způsob, jak předem zjistit, co služba adresu nebo identifikátor URI (Uniform Resource), bude. Místo pevně kódováno adresu, je vhodnější umožňují správcům udělat po vytvoření služby. Tato možnost se provádí prostřednictvím konfigurace.  
  
> [!NOTE]
>  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config` přepínač tak, aby rychle vytvořit konfigurační soubory.  
  
## <a name="major-sections"></a>Hlavní části  
 Schéma konfigurace Windows Communication Foundation (WCF) zahrnuje následující tři hlavní oddíly (`serviceModel`, `bindings`, a `services`):  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a>Elementy ServiceModel  
 Můžete použít v části ohraničené `system.ServiceModel` elementu, který chcete nakonfigurovat jeden nebo více koncových bodů, jakož i nastavení služby typu služby. Každý koncový body, můžete pak nakonfigurovat s adresu, kontrakt a vazbu. Další informace o koncových bodech najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md). Pokud nejsou zadány žádné koncové body, modul runtime přidá výchozí koncové body. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Vazba určuje přenosy (HTTP, TCP, kanály, služby Řízení front zpráv) a protokoly (zabezpečení, spolehlivost, transakce toky) a se skládá z elementů, z nichž každý určuje aspekt jak koncový bod komunikuje s ostatními vazby.  
  
 Například zadání [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element označuje na používání protokolu HTTP jako přenosu pro koncový bod. To se používá k přenosu do koncového bodu v době běhu, když je otevřen služby pomocí tento koncový bod.  
  
 Existují dva typy vazeb: předdefinované a vlastní. Předdefinované vazby obsahovat užitečné kombinace elementů, které se používají v běžné scénáře. Seznam předdefinovaných vazby typy, které poskytuje WCF najdete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md). Pokud žádná vazba předdefinované kolekce má správnou kombinaci funkcí, které potřebuje aplikace služby, můžete vytvořit vlastní vazby splnění aplikace. Další informace o vlastních vazeb najdete v tématu [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Následující čtyři příklady ilustrují nejběžnější konfigurace vazby používá pro nastavení služby WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Určení použít typ vazby koncového bodu  
 V prvním příkladu znázorňuje, jak zadat koncovým bodem nakonfigurovaným s adresu, kontrakt a vazbu.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 V tomto příkladu `name` atribut určuje, jaký typ služby, konfigurace je pro. Při vytváření služby v kódu pomocí `HelloWorld` kontrakt, je inicializován s koncové body definované v příklad konfigurace. Pokud sestavení implementuje pouze jeden kontrakt služby, `name` atribut můžete tento parametr vynechán, protože služba používá k dispozici pouze typu. Atribut přebírá řetězec, který musí být ve formátu `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Atribut určuje identifikátor URI, který ostatní koncové body, používat pro komunikaci ve službě. Identifikátor URI může být absolutní nebo relativní cestu. Pokud je zadaný relativní adresa, hostitel se očekává poskytování základní adresu, která je vhodná pro používané vazba schéma přenosu. Pokud adresa není nakonfigurována, základní adresu se považuje za adresu pro tohoto koncového bodu.  
  
 `contract` Atribut určuje kontrakt tento koncový bod je vystavení. Typ implementace služby musí implementovat typ smlouvy. Pokud implementace služby implementuje typu jeden kontrakt, můžete tuto vlastnost vynechat.  
  
 `binding` Atribut vybere předdefinované nebo vlastní vazby má použít pro tento konkrétní koncový bod. Koncový bod, který není explicitně vyberte vazbu používá výchozí výběr vazby, což je `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Úprava předdefinované vazby  
 V následujícím příkladu je upravit vazbu předdefinované. Ji pak slouží ke konfiguraci žádný koncový bod služby. Vazba je upravena podle nastavení <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> hodnotu na 1 sekundu. Všimněte si, že vlastnost vrací <xref:System.TimeSpan> objektu.  
  
 Který změnit vazby naleznete v části vazby. Změnit vazby lze nyní použít při vytváření žádný koncový bod, a to nastavením `binding` atribut `endpoint` elementu.  
  
> [!NOTE]
>  Pokud přiřadíte konkrétní název pro vazba, `bindingConfiguration` zadané v rámci služby koncový bod se musí shodovat s ním.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Konfigurace chování chcete použít pro služby  
 V následujícím příkladu je konkrétní chování nakonfigurován pro typ služby. `ServiceMetadataBehavior` Element slouží k povolení [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zadat dotaz na službu a generovat webové služby popis Language (WSDL) dokumenty z metadat.  
  
> [!NOTE]
>  Pokud přiřadíte konkrétní název v chování `behaviorConfiguration` zadaný v služba nebo koncový bod oddíl se musí shodovat se.  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 Předchozí konfigurace umožňuje klient volání a získat metadata "HelloWorld" zadali služby.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Určení služby s dva koncové body pomocí hodnot jinou vazbou  
 V tomto příkladu poslední dva koncové body pro nakonfigurovaných `HelloWorld` typ služby. Každý koncový bod používá jiné přizpůsobit `bindingConfiguration` atribut stejný typ vazby (každý upraví `basicHttpBinding`).  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 Můžete získat pomocí výchozí konfigurace přidáním stejné chování `protocolMapping` části a konfiguraci vazby, jak je ukázáno v následujícím příkladu.  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a>Viz také  
 [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)  
 [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)  
 [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
