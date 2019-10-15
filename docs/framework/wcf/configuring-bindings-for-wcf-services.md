---
title: Konfigurace vazeb pro služby Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 92f9457dd0c118c9a7c578a7088f66cdea1e5ad0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320671"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a>Konfigurace vazeb pro služby Windows Communication Foundation
Při vytváření aplikace často chcete po nasazení aplikace odložit rozhodnutí správci. Například neexistuje žádný způsob, jak si předem zjistit, jakou adresu služby nebo identifikátor URI (Uniform Resource Identifier). Místo hardwarového zakódování adresy je vhodnější dát správcům po vytvoření služby. Tato flexibilita je zajištěna prostřednictvím konfigurace.  
  
> [!NOTE]
> K rychlému vytvoření konfiguračních souborů použijte [Nástroj Svcutil. exe (. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) s přepínačem `/config`.  
  
## <a name="major-sections"></a>Hlavní oddíly  
 Schéma konfigurace Windows Communication Foundation (WCF) obsahuje následující tři hlavní oddíly (`serviceModel`, `bindings` a `services`):  
  
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
  
### <a name="servicemodel-elements"></a>ServiceModel – prvky  
 Můžete použít oddíl ohraničený prvkem `system.ServiceModel` ke konfiguraci typu služby s jedním nebo více koncovými body a také s nastavením pro službu. U každého koncového bodu se pak dá nakonfigurovat adresa, kontrakt a vazba. Další informace o koncových bodech najdete v tématu [Přehled vytváření koncových](endpoint-creation-overview.md)bodů. Pokud nejsou zadány žádné koncové body, modul runtime přidá výchozí koncové body. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
 Vazba určuje přenosy (HTTP, TCP, kanály, řízení front zpráv) a protokoly (zabezpečení, spolehlivost, toky transakcí) a skládá se z elementů vazby, z nichž každý určuje aspekt způsobu komunikace koncového bodu s celým světem.  
  
 Například určení prvku [> \<basicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md) označuje, že se má jako přenos pro koncový bod používat protokol HTTP. Tento postup se používá k navýšení koncového bodu v době běhu, kdy je otevřená služba používající tento koncový bod.  
  
 Existují dva druhy vazeb: předdefinované a vlastní. Předdefinované vazby obsahují užitečné kombinace prvků, které se používají v běžných scénářích. Seznam předdefinovaných typů vazeb, které poskytuje WCF, najdete v tématu [vazby poskytované systémem](system-provided-bindings.md). Pokud žádná předdefinovaná kolekce vazeb nemá správnou kombinaci funkcí, které potřebuje aplikace služby, můžete vytvořit vlastní vazby, které splňují požadavky aplikace. Další informace o vlastních vazbách naleznete v tématu [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md).  
  
 Následující čtyři příklady ilustrují nejběžnější konfigurace vazeb používané pro nastavení služby WCF.  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a>Zadání koncového bodu pro použití typu vazby  
 První příklad ukazuje, jak zadat koncový bod nakonfigurovaný s adresou, kontraktem a vazbou.  
  
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
  
 V tomto příkladu atribut `name` označuje, pro který typ služby se konfigurace používá. Při vytváření služby v kódu s kontraktem `HelloWorld` se inicializuje se všemi koncovými body definovanými v ukázkové konfiguraci. Pokud sestavení implementuje pouze jeden kontrakt služby, může být atribut `name` vynechán, protože služba používá pouze dostupný typ. Atribut přebírá řetězec, který musí být ve formátu `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`.  
  
 Atribut `address` určuje identifikátor URI, který používají jiné koncové body ke komunikaci se službou. Identifikátor URI může být buď absolutní, nebo relativní cesta. Pokud je zadána relativní adresa, očekává se, že hostitel poskytne základní adresu, která je vhodná pro přenosové schéma používané ve vazbě. Pokud není adresa nakonfigurovaná, předpokládá se, že základní adresa je adresa pro tento koncový bod.  
  
 Atribut `contract` určuje kontrakt, který tento koncový bod zveřejňuje. Typ implementace služby musí implementovat typ kontraktu. Pokud implementace služby implementuje jeden typ kontraktu, může být tato vlastnost vynechána.  
  
 Atribut `binding` vybírá předdefinovanou nebo vlastní vazbu, která se má použít pro tento konkrétní koncový bod. Koncový bod, který explicitně nevybere vazbu, používá výchozí výběr vazby, který je `BasicHttpBinding`.  
  
#### <a name="modifying-a-predefined-binding"></a>Úprava předdefinované vazby  
 V následujícím příkladu je upravena předdefinovaná vazba. Pak ji můžete použít ke konfiguraci libovolného koncového bodu ve službě. Vazba je upravena nastavením hodnoty <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> na 1 sekundu. Všimněte si, že vlastnost vrací objekt <xref:System.TimeSpan>.  
  
 Změněné vazby najdete v části Bindings. Tato změněná vazba se teď dá použít při vytváření libovolného koncového bodu nastavením atributu `binding` v prvku `endpoint`.  
  
> [!NOTE]
> Pokud pro vazbu udělíte konkrétní název, `bindingConfiguration` zadaný v koncovém bodu služby se musí shodovat s ní.  
  
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
 V následujícím příkladu je pro typ služby nakonfigurováno konkrétní chování. Element `ServiceMetadataBehavior` slouží k povolení [Nástroje pro DoSvcutilení metadat (ServiceModel](servicemodel-metadata-utility-tool-svcutil-exe.md) ) pro dotazování služby a generování dokumentů jazyka WSDL (Web Services Description Language) z metadat.  
  
> [!NOTE]
> Pokud tomuto chování udělíte konkrétní název, `behaviorConfiguration` zadaný v sekci služby nebo koncového bodu se musí shodovat.  
  
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
  
 Předchozí konfigurace umožňuje klientovi volat a získat metadata služby typovaného typu HelloWorld.  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a>Určení služby se dvěma koncovými body pomocí různých hodnot vazeb  
 V tomto posledním příkladu jsou pro typ služby `HelloWorld` nakonfigurovány dva koncové body. Každý koncový bod používá jiný přizpůsobený atribut `bindingConfiguration` stejného typu vazby (každé upraví `basicHttpBinding`).  
  
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
  
 Stejné chování můžete získat pomocí výchozí konfigurace přidáním části `protocolMapping` a konfigurací vazeb, jak je znázorněno v následujícím příkladu.  
  
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

- [Zjednodušená konfigurace](simplified-configuration.md)
- [Vazby poskytované systémem](system-provided-bindings.md)
- [Přehled vytváření koncových bodů](endpoint-creation-overview.md)
- [Používání vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md)
