---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 8fdae02b558708a9b3f4535123752dce12dd5cf5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153137"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<přidat> \<baseAddressPrefixFilter>
Představuje konfigurační prvek, který určuje předávací filtr, který poskytuje mechanismus pro výběr vhodných vazeb Internetové informační služby (IIS) při hostování aplikace WCF (Windows Communication Foundation) ve službě IIS.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Předponu|Identifikátor URI, který se používá k porovnejte část základní adresy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Kolekce konfiguračních prvků, které určují předávací filtry, které poskytují mechanismus pro výběr vhodných vazeb služby IIS při hostování aplikace WCF (Windows Communication Foundation) ve službě IIS.|  
  
## <a name="remarks"></a>Poznámky  
 Filtr předpony poskytuje poskytovatelům sdíleného hostingu způsob, jak určit, které identifikátory URI mají být službou používány. Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma na stejném webu.  
  
 Weby služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře. Aplikace v lokalitě je přístupná prostřednictvím jedné nebo více vazeb služby IIS. Vazby iis poskytují dvě informace: závazný protokol a informace o vazbě. Protokol vazby (například HTTP) definuje schéma, přes které dochází ke komunikaci, a informace o vazbě (například IP adresa, port, hlavička hostitele) obsahují data použitá pro přístup k webu.  
  
 IIS podporuje určení více vazeb iis pro každou lokalitu, což má za následek více základních adres pro každé schéma. Vzhledem k tomu, že služba WCF hostovaná pod webem umožňuje vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpony vybrat požadovanou základní adresu hostované služby. Příchozí základní adresy dodané službou IIS jsou filtrovány na základě volitelného filtru seznamu předponami.  
  
 Web může například obsahovat následující základní adresy:
  
```
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény aplikace.  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 V tomto `net.tcp://test1.fabrikam.com:8000` příkladu a `http://test2.fabrikam.com:9000` jsou pouze základní adresy pro jejich příslušné systémy, které mohou být předány.  
  
 Ve výchozím nastavení není zadána předpona, jsou předány všechny adresy. Zadání předpony umožňuje pouze odpovídající základní adresu pro toto schéma, které mají být předány.  
  
> [!NOTE]
> Filtr nepodporuje žádné zástupné znaky. Kromě toho baseAddresses poskytované iIS může mít adresy vázané na jiná `baseAddressPrefixFilters` schémata, které nejsou k dispozici v seznamu. Tyto adresy nejsou odfiltrovány.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hostování](../../../wcf/feature-details/hosting.md)
