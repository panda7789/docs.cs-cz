---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 09a796a78cf37b464f5f7c359822d9d0c5001787
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362406"
---
# <a name="servicehostingenvironment"></a>\<serviceHostingEnvironment>
Tento prvek definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos. Pokud tento prvek je prázdný, je použit výchozí typ. Tento prvek jde použít jenom na aplikace nebo na úrovni konfigurační soubory.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|Logická hodnota označující, zda režim kompatibility ASP.NET je zapnutý pro aktuální aplikaci. Výchozí hodnota je `false`.<br /><br /> Když tento atribut je nastaven na `true`požadavků na služby Windows Communication Foundation (WCF) tok prostřednictvím kanálu HTTP technologie ASP.NET a komunikaci přes protokoly jiným protokolem než HTTP je zakázaná. Další informace najdete v tématu [služby WCF a ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|Celé číslo určující minimální množství volné paměti, která má být k dispozici systému, před aktivací služby WCF. **Upozornění:**  Zadání tohoto atributu společně s částečnou důvěryhodností v souboru web.config služby WCF způsobí <xref:System.Security.SecurityException> při spuštění služby.|  
|multipleSiteBindingsEnabled|Logická hodnota, která určuje, zda je povoleno více vazeb služby IIS webu.<br /><br /> IIS se skládá z webů, které jsou kontejnery pro virtuální aplikace obsahující virtuální adresáře. Aplikace v síti přístupné prostřednictvím jednoho nebo více vazeb služby IIS. Vazby služby IIS poskytuje dva druhy údajů: protokol vazby a informace o vazbě. Vazba protokolu definuje schéma, přes které probíhá komunikace a informace o vazbě je informace, které slouží pro přístup k webu. Příklad vazby protokolu může být HTTP, kdežto informace o vazbě může obsahovat IP adresu, Port, hlavičku hostitele, atd.<br /><br /> Služba IIS podporuje zadávání více vazeb služby IIS webu, což vede k více základních adres na jedno schéma. Hostované na webu služby Windows Communication Foundation (WCF) umožňuje však vazba pouze jedna vlastnost baseAddress jedno schéma.<br /><br /> Pokud chcete povolit více vazeb služby IIS webu pro službu Windows Communication Foundation (WCF), tento atribut nastavte na `true`. Všimněte si, že více vazeb webu se podporuje jenom pro protokol HTTP. Adresy koncových bodů v konfiguračním souboru musí být úplný identifikátor URI.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Kolekci konfiguračních elementů určujících předponu filtry pro základní adresy použité hostitelem služby.|  
|[\<serviceActivations>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Konfigurační oddíl, který popisuje nastavení aktivace.|  
|[\<transportConfigurationTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Kolekce elementů konfigurace, které určují typ konkrétní přenos.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|serviceModel|Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení služby WCF spuštění – souběžně s rozhraním ASP.NET v prostředí domény aplikace (AppDomain). I když WCF a ASP.NET mohou existovat vedle sebe v téže doméně AppDomain, WCF požadavky nejsou zpracovávány kanálu HTTP ASP.NET ve výchozím nastavení. Několik prvků platformy aplikace ASP.NET v důsledku toho nejsou k dispozici ke službám WCF. Patří mezi ně  
  
-   Autorizace souboru nebo adresy URL technologie ASP.NET  
  
-   ASP.NET Impersonation  
  
-   Stav relace na základě souboru cookie  
  
-   HttpContext.Current  
  
-   Kanál rozšiřitelnost prostřednictvím vlastních modulu HttpModule  
  
 Pokud vaše služby WCF potřebujete pracovat v rámci technologie ASP.NET a komunikovat jenom přes protokol HTTP, můžete použít režim kompatibility ASP.NET na WCF. Když je zapnutý tento režim `aspNetCompatibilityEnabled` atribut je nastaven na `true` na úrovni aplikace. Implementace služby musí deklarovat své možnost spouštět pomocí režimu kompatibility <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> třídy. Když je povolený režim kompatibility,  
  
-   Autorizace souboru nebo adresy URL technologie ASP.NET je vynuceno před WCF autorizace. Rozhodnutí o autorizaci vychází transportní vrstvy identitu požadavku. Identit na úrovni zprávy jsou ignorovány.  
  
-   Operací služby WCF start ke spuštění v kontextu zosobnění technologie ASP.NET. Pokud je pro konkrétní službu povolené zosobnění technologie ASP.NET a WCF zosobnění, platí kontextu zosobnění WCF.  
  
-   HttpContext.Current je možné z kódu služby WCF a služeb bránit zveřejnění jiným protokolem než HTTP koncových bodů.  
  
-   WCF jsou zpracovány pomocí kanálu ASP.NET. HttpModules, které jsou nakonfigurované tak, aby fungoval na příchozí požadavky může také zpracovat WCF žádosti. Může jít o komponenty platformy technologie ASP.NET (například <xref:System.Web.SessionState.SessionStateModule>), a také vlastní třetích stran moduly.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak povolit režim kompatibility ASP.  
  
## <a name="code"></a>Kód  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hostování](../../../../../docs/framework/wcf/feature-details/hosting.md)
- [Služby WCF a ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
