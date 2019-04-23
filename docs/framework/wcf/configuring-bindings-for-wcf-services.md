---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 009011100af86e315aa41beb822b1448e2f21b25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150446"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurace vazeb pro služby Windows Communication Foundation
Při vytváření aplikace, často chcete odložit rozhodnutí, která správci po nasazení aplikace. Například není často předem vědět, co adresu služby, nebo identifikátor URI (Uniform Resource), budou. Místo pevného kódování adresu, je vhodnější umožňují správcům udělat po vytvoření služby. Díky této flexibilitě se provádí prostřednictvím konfigurace.  
  
> [!NOTE]
>  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config` přepínač tak, aby rychle vytvořit konfigurační soubory.  
  
## <a name="major-sections"></a>Major Sections  
 Schéma konfigurace Windows Communication Foundation (WCF) zahrnuje následující tři hlavní části (`serviceModel`, `bindings`, a `services`):  
  
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
  
### <a name="servicemodel-elements"></a>Prvky ServiceModel  
 Můžete použít části ohraničené `system.ServiceModel` element konfigurace typu služby pomocí jednoho nebo víc koncových bodů, nastavení služby. Každý koncový bod může být nakonfigurována s adresou, kontrakt a vazby. Další informace o koncových bodech najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md). Pokud nejsou zadány žádné koncové body, modulu runtime přidá výchozí koncové body. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
 Vazbu určuje přenosy (HTTP, TCP, kanály, služby Řízení front zpráv) a protokoly (zabezpečení, spolehlivost, transakce toky) a skládá se z elementů, z nichž každý Určuje určitý aspekt jak koncový bod komunikuje s ostatními vazby.  
  
 Například zadání [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) určuje element na používání protokolu HTTP jako přenosu pro koncový bod. To se používá k přenosu do koncového bodu v době běhu, když se otevře pomocí tohoto koncového bodu služby.  
  
 Existují dva typy vazeb: předdefinované a vlastní. Předdefinovaných vazeb obsahují užitečné kombinaci prvků, které se používají v běžné scénáře. Seznam typů předdefinovaných vazeb, které poskytuje WCF najdete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md). Pokud žádná vazba předdefinované kolekce nemá správnou kombinaci funkcí, které musí aplikace služby, můžete vytvořit vlastní vazby pro splnění požadavků vaší aplikace. Další informace o vlastních vazeb naleznete v tématu [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
 Následující čtyři příklady ilustrují nejběžnější konfigurace vazby používá pro nastavení služby WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Zadání koncového bodu používat typ vazby  
 První příklad ukazuje, jak zadat koncový bod nakonfigurovaný s adresou, kontrakt a vazby.  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 V tomto příkladu `name` atribut označuje, jaký typ služby, je konfigurace pro. Při vytváření služby v kódu s `HelloWorld` smlouvy, je inicializována s všechny koncové body definované v konfiguraci příklad. Pokud sestavení implementuje pouze jeden kontrakt služby `name` atribut lze vynechat, protože služba využívá typ pouze k dispozici. Atribut přijímá řetězec, který musí být ve formátu `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 `address` Atribut určuje identifikátor URI, který ostatní koncové body používat pro komunikaci ve službě. Identifikátor URI může být absolutní nebo relativní cestu. Pokud je zadána relativní adresa, hostitel se očekává poskytování základní adresa, která je vhodná pro schéma přepravy používá ve vazbě. Pokud není konfigurována adresa, základní adresa je považován za adresu pro tento koncový bod.  
  
 `contract` Atribut určuje kontrakt tento koncový bod vystavuje. Typ implementace služby musí implementovat typ kontraktu. Pokud implementace služby implementuje typ jeden kontrakt, lze tuto vlastnost vynechat.  
  
 `binding` Atribut vybere předdefinovaných nebo vlastních vazbu pro tento konkrétní koncový bod. Koncový bod, který není explicitně zvolená vazby používá vazbu výchozí výběr, který je `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Úprava předdefinovaných vazeb  
 V následujícím příkladu je upraven předdefinované vazby. Ji pak slouží ke konfiguraci libovolný koncový bod služby. Vazba je upravit tak, že nastavíte <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> hodnotu na 1 sekundu. Všimněte si, že vlastnost vrací <xref:System.TimeSpan> objektu.  
  
 Který změnit vazby najdete v části vazeb. To změnit vazby se teď dá při vytváření libovolný koncový bod tak, že nastavíte `binding` atribut `endpoint` elementu.  
  
> [!NOTE]
>  Pokud dáte konkrétní název vazby, `bindingConfiguration` zadaný ve službě koncový bod se musí shodovat s ním.  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Konfigurace chování má použít pro služby  
 V následujícím příkladu je nakonfigurované konkrétní chování pro typ služby. `ServiceMetadataBehavior` Element slouží k povolení [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k dotazování na službu a generovat webové služby WSDL (Description Language) dokumenty z metadat.  
  
> [!NOTE]
>  Pokud musíte pojmenovat konkrétní chování, `behaviorConfiguration` podle služba nebo koncový bod oddílu odpovídat.  
  
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
  
 Předchozí konfigurace umožňuje klient volat a získat metadata "HelloWorld" typu služby.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Určení služby pomocí dva koncové body pomocí hodnoty jinou vazbou  
 V tomto příkladu poslední dva koncové body se konfigurují pro `HelloWorld` typ služby. Každý koncový bod používá jiný přizpůsobit `bindingConfiguration` atribut stejný typ vazby (každý upraví `basicHttpBinding`).  
  
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
  
 Můžete získat stejné chování pomocí výchozí konfigurace tak, že přidáte `protocolMapping` oddílu a konfigurace vazby, jak je ukázáno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md)
- [Vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md)
- [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
