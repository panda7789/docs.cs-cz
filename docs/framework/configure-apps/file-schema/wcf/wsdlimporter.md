---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 317921a66fa3b8d1f0026d676ea674b67732b3df
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854755"
---
# <a name="wsdlimporter"></a>\<wsdlImporter>
Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> metadat**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsdlImporters >** ](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<WsdlImporter nalezl >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`type`|Typ tohoto prvku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|Určuje všechny nástroje pro Import WSDL, které importují metadata jazyka WSDL (Web Services Description Language) 1,1 s přílohami WS-Policy.|  
  
## <a name="remarks"></a>Poznámky  
 Import WSDL slouží k importu metadat a také k převedení těchto informací do různých tříd, které reprezentují informace o kontraktech a koncových bodech. Může selektivně importovat informace o kontraktech a koncových bodech a vlastnosti, které zveřejňují chyby importu a přijímají informace o typu relevantní pro proces importu a převodu. Podporuje také import informací o vazbách a vlastností, které poskytují přístup k jakýmkoli dokumentům zásad, dokumentům WSDL, rozšířením WSDL a dokumentům XML schématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [Konfigurace klienta WCF](../../../wcf/feature-details/client-configuration.md)
- [Klienti](../../../wcf/feature-details/clients.md)
