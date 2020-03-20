---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174820"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurace vazeb pro služby Windows Communication Foundation
Při vytváření aplikace, často chcete odložit rozhodnutí správce po nasazení aplikace. Například často neexistuje žádný způsob, jak předem zjistit, jaká bude adresa služby nebo identifikátor URI (Uniform Resource Identifier). Místo pevného kódování adresy je vhodnější povolit správci, aby tak učinil po vytvoření služby. Tato flexibilita se provádí prostřednictvím konfigurace.  
  
> [!NOTE]
> Pomocí [nástroje ServiceModel Metadata Utility Tool Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) s přepínačem `/config` můžete rychle vytvářet konfigurační soubory.  
  
## <a name="major-sections"></a>Hlavní sekce  
 Schéma konfigurace Windows Communication Foundation (WCF) zahrnuje`serviceModel`následující `bindings`tři `services`hlavní oddíly ( , , a ):  
  
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
  
### <a name="servicemodel-elements"></a>Prvky modelu service  
 Oddíl ohraničený elementem `system.ServiceModel` můžete použít ke konfiguraci typu služby s jedním nebo více koncovými body a také nastavením služby. Každý koncový bod pak lze nakonfigurovat s adresou, smlouvy a vazby. Další informace o koncových bodech naleznete v [tématu Přehled vytváření koncových bodů](endpoint-creation-overview.md). Pokud nejsou zadány žádné koncové body, runtime přidá výchozí koncové body. Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
 Vazba určuje přenosy (HTTP, TCP, kanály, řízení front zpráv) a protokoly (zabezpečení, spolehlivost, toky transakcí) a skládá se z elementů vazby, z nichž každý určuje aspekt způsobu komunikace koncového bodu se světem.  
  
 Například zadání [ \<elementu basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) označuje použití protokolu HTTP jako přenosu pro koncový bod. Používá se k drátu koncového bodu v době běhu při otevření služby pomocí tohoto koncového bodu.  
  
 Existují dva druhy vazeb: předdefinované a vlastní. Předdefinované vazby obsahují užitečné kombinace prvků, které se používají v běžných scénářích. Seznam předdefinovaných typů vazeb, které poskytuje WCF, naleznete v [tématu Vazby poskytované systémem](system-provided-bindings.md). Pokud žádná předdefinovaná kolekce vazeb má správnou kombinaci funkcí, které aplikace služby potřebuje, můžete vytvořit vlastní vazby tak, aby splňovaly požadavky aplikace. Další informace o vlastní vazby naleznete [ \<v tématu customBinding>](../configure-apps/file-schema/wcf/custombinding.md).  
  
 Následující čtyři příklady ilustrují nejběžnější konfigurace vazby používané pro nastavení služby WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Určení koncového bodu pro použití typu vazby  
 První příklad ukazuje, jak určit koncový bod nakonfigurovaný s adresou, smlouvou a vazbou.  
  
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
  
 V tomto příkladu `name` atribut označuje, pro který typ služby je konfigurace. Když vytvoříte službu v `HelloWorld` kódu se smlouvou, je inicializována se všemi koncovými body definovanými v konfiguraci příkladu. Pokud sestavení implementuje pouze jednu servisní smlouvu, `name` atribut lze vynechat, protože služba používá pouze dostupný typ. Atribut přebírá řetězec, který musí být ve formátu`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`  
  
 Atribut `address` určuje identifikátor URI, který ostatní koncové body používají ke komunikaci se službou. Identifikátor URI může být absolutní nebo relativní cesta. Pokud je k dispozici relativní adresa, očekává se, že hostitel poskytne základní adresu, která je vhodná pro schéma přenosu použité ve vazbě. Pokud adresa není nakonfigurována, předpokládá se, že základní adresa je adresa pro tento koncový bod.  
  
 Atribut `contract` určuje kontrakt, který tento koncový bod vystavuje. Typ implementace služby musí implementovat typ smlouvy. Pokud implementace služby implementuje jeden typ smlouvy, pak tuto vlastnost lze vynechat.  
  
 Atribut `binding` vybere předdefinovanou nebo vlastní vazbu, která se použije pro tento konkrétní koncový bod. Koncový bod, který explicitně nevybere vazbu, používá `BasicHttpBinding`výchozí výběr vazby, což je .  
  
#### <a name="modifying-a-predefined-binding"></a>Úprava předdefinované vazby  
 V následujícím příkladu je změněna předdefinovaná vazba. Potom lze nakonfigurovat libovolný koncový bod ve službě. Vazba je změněna <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> nastavením hodnoty na 1 sekundu. Všimněte si, <xref:System.TimeSpan> že vlastnost vrátí objekt.  
  
 Tato změněná vazba se nachází v části vazby. Tuto změněnou vazbu lze nyní použít při `binding` vytváření libovolného koncového bodu nastavením atributu `endpoint` v prvku.  
  
> [!NOTE]
> Pokud zadáváte určitý název vazby, `bindingConfiguration` zadaný v koncovém bodu služby musí odpovídat s ním.  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a>Konfigurace chování, které se má použít u služby  
 V následujícím příkladu je pro typ služby nakonfigurováno určité chování. Prvek `ServiceMetadataBehavior` se používá k povolení [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) k dotazování služby a generování webových služeb Description Language (WSDL) dokumenty z metadat.  
  
> [!NOTE]
> Pokud přidáváte určitý název chování, `behaviorConfiguration` zadaný v části služby nebo koncového bodu musí odpovídat.  
  
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
  
 Předchozí konfigurace umožňuje klientovi volat a získat metadata služby "HelloWorld" zadali.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Určení služby se dvěma koncovými body pomocí různých hodnot vazby  
 V tomto posledním příkladu jsou pro `HelloWorld` typ služby nakonfigurovány dva koncové body. Každý koncový bod používá `bindingConfiguration` jiný přizpůsobený atribut stejného typu vazby (každý upravuje `basicHttpBinding`).  
  
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
  
 Stejné chování pomocí výchozí konfigurace můžete získat `protocolMapping` přidáním oddílu a konfigurací vazeb, jak je znázorněno v následujícím příkladu.  
  
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

- [Zjednodušená konfigurace](simplified-configuration.md)
- [Vazby poskytované systémem](system-provided-bindings.md)
- [Přehled vytváření koncových bodů](endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
