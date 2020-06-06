---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 165dbed1b78d00f8d4dd3e482b9fee8a23db60da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399617"
---
# \<serviceHostingEnvironment>
Tento prvek definuje typ, který hostující prostředí služby vytvoří pro konkrétní přenos. Pokud je tento prvek prázdný, je použit výchozí typ. Tento element lze použít pouze v konfiguračních souborech aplikace nebo na úrovni počítače.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
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
|aspNetCompatibilityEnabled|Logická hodnota označující, zda byl v aktuální aplikaci zapnut režim kompatibility ASP.NET. Výchozí formát je `false`.<br /><br /> Pokud je tento atribut nastaven na hodnotu `true` , požadavky na služby Windows Communication Foundation (WCF) tok prostřednictvím kanálu HTTP ASP.NET a komunikace přes protokoly bez protokolu HTTP je zakázaná. Další informace najdete v tématu [služby WCF a ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).|  
|Služby minFreeMemoryPercentageToActivateService|Celé číslo, které určuje minimální velikost volné paměti, která by měla být k dispozici systému, než bude možné aktivovat službu WCF. **Upozornění:**  Zadání tohoto atributu společně s částečným vztahem důvěryhodnosti v souboru Web. config služby WCF bude mít za následek <xref:System.Security.SecurityException> spuštění služby.|  
|multipleSiteBindingsEnabled|Logická hodnota, která určuje, zda je povoleno více vazeb služby IIS na jednom webu.<br /><br /> Služba IIS se skládá z webů, které jsou kontejnery pro virtuální aplikace obsahující virtuální adresáře. Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS. Vazba služby IIS poskytuje dvě části informací: protokol vazby a informace o vazbě. Protokol vazby definuje schéma, přes které probíhá komunikace, a informace o vazbě, které slouží k přístupu k webu. Příkladem protokolu vazby může být HTTP, zatímco informace o vazbě můžou obsahovat IP adresu, port, hlavičku hostitele atd.<br /><br /> Služba IIS podporuje zadání více vazeb služby IIS na jeden web, což vede k vytvoření více základních adres na schéma. Služba Windows Communication Foundation (WCF) hostovaná v lokalitě však umožňuje vytvořit vazbu pouze na jednu hodnotu baseAddress na schéma.<br /><br /> Chcete-li povolit více vazeb služby IIS na webu pro službu Windows Communication Foundation (WCF), nastavte tento atribut na hodnotu `true` . Všimněte si, že více vazeb webu je podporováno pouze pro protokol HTTP. Adresa koncových bodů v konfiguračním souboru musí být úplný identifikátor URI.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Kolekce elementů konfigurace, které určují filtry předpony pro základní adresy používané hostitelem služby.|  
|[\<serviceActivations>](serviceactivations.md)|Konfigurační oddíl, který popisuje nastavení aktivace.|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|Kolekce elementů konfigurace, které identifikují typ konkrétního přenosu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|serviceModel|Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou služby WCF spouštěny souběžně s ASP.NET v doménách hostované aplikace (AppDomain). I když WCF a ASP.NET můžou existovat ve stejné doméně AppDomain, požadavky WCF nejsou ve výchozím nastavení zpracovávány kanálem HTTP ASP.NET. V důsledku toho nejsou služby WCF k dispozici několik prvků aplikace ASP.NET Application Platform. Mezi ně patří  
  
- ASP.NET/autorizace adresy URL  
  
- Zosobnění technologie ASP.NET  
  
- Stav relace na základě souborů cookie  
  
- HttpContext. Current  
  
- Rozšiřitelnost kanálu prostřednictvím vlastního HttpModuleu  
  
 Pokud vaše služby WCF potřebují fungovat v kontextu ASP.NET a komunikují pouze přes protokol HTTP, můžete použít režim kompatibility WCF ASP.NET. Tento režim je zapnutý, když `aspNetCompatibilityEnabled` je atribut nastavený na `true` úrovni aplikace. Implementace služeb musí deklarovat jejich schopnost spouštět v režimu kompatibility pomocí <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> třídy. Pokud je povolen režim kompatibility,  
  
- Před autorizací WCF se vynutila autorizace souboru nebo adresy URL ASP.NET. Rozhodnutí o autorizaci vychází z identity na úrovni přenosu. Identity na úrovni zprávy se ignorují.  
  
- Operace služby WCF se začnou spouštět v kontextu zosobnění ASP.NET. Pokud jsou pro konkrétní službu povolené zosobnění ASP.NET a zosobnění WCF, použije se kontext zosobnění WCF.  
  
- Vlastnost HttpContext. Current lze použít z kódu služby WCF. služby zabraňují úniku koncových bodů mimo HTTP.  
  
- Požadavky služby WCF zpracovává kanál ASP.NET. HttpModules, které byly nakonfigurovány na zpracování příchozích požadavků, mohou také zpracovávat požadavky WCF. Mezi ně můžou patřit komponenty platformy ASP.NET (například <xref:System.Web.SessionState.SessionStateModule> ) a také vlastní moduly třetích stran.  
  
## <a name="example"></a>Příklad  
 Následující ukázka kódu ukazuje, jak povolit režim kompatibility ASP.  
  
## <a name="code"></a>Kód  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
- [Služby WCF a ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md)
