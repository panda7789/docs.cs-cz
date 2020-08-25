---
title: <add> z <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: 2572a6ee6763ae26fe5c56669e10f8c9aef8a280
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811792"
---
# <a name="add-of-baseaddressprefixfilter"></a>\<add> z \<baseAddressPrefixFilter>
Představuje prvek konfigurace, který určuje předávací filtr, který poskytuje mechanismus pro výběr příslušných vazeb Internetová informační služba (IIS) při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Syntax  
  
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
|směr|Identifikátor URI, který se používá k vyhledání části základní adresy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|Kolekce elementů konfigurace, které určují předávací filtry, které poskytují mechanismus pro výběr příslušných vazeb služby IIS při hostování aplikace Windows Communication Foundation (WCF) ve službě IIS.|  
  
## <a name="remarks"></a>Poznámky  
 Filtr předpon poskytuje způsob, jak sdíleným poskytovatelům hostingu určit, které identifikátory URI bude služba používat. Umožňuje sdíleným hostitelům hostovat více aplikací s různými základními adresami pro stejné schéma ve stejné lokalitě.  
  
 Webové stránky služby IIS jsou kontejnery pro virtuální aplikace, které obsahují virtuální adresáře. Aplikace v lokalitě je k dispozici prostřednictvím jedné nebo více vazeb služby IIS. Vazby služby IIS poskytují dvě informace: vazby protokolu a informace o vazbě. Protokol vazby (například HTTP) definuje schéma, přes které probíhá komunikace, a informace o vazbě (například IP adresa, port, hostheader) obsahuje data, která se používají pro přístup k webu.  
  
 Služba IIS podporuje zadání více vazeb služby IIS pro každou lokalitu, což má za následek více základních adres pro každé schéma. Vzhledem k tomu, že služba WCF hostovaná v rámci lokality umožňuje vytvořit vazbu pouze na jednu základní adresu pro každé schéma, můžete pomocí funkce filtru předpon vybrat požadovanou základní adresu hostované služby. Příchozí základní adresy, které poskytuje služba IIS, se filtrují na základě volitelného filtru seznamu předpon.  
  
 Například váš web může obsahovat následující základní adresy:
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 Následující konfigurační soubor můžete použít k určení filtru předpony na úrovni domény AppDomain.  
  
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
  
 V tomto příkladu `net.tcp://test1.fabrikam.com:8000` `http://test2.fabrikam.com:9000` jsou jedinými základními adresami pro jejich příslušné systémy, které mohou být předány.  
  
 Ve výchozím nastavení, pokud není zadána předpona, jsou předány všechny adresy. Zadání předpony umožňuje předávat odpovídající základní adresu pro toto schéma.  
  
> [!NOTE]
> Filtr nepodporuje žádné zástupné znaky. Kromě toho adres BaseAddresses poskytované službou IIS může mít adresy svázané s jinými schématy, která nejsou přítomna v `baseAddressPrefixFilters` seznamu. Tyto adresy nejsou vyfiltrovány.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [Hosting](../../../wcf/feature-details/hosting.md)
