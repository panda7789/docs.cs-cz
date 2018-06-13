---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 33c2b0e4286ce746f745e4aebe10fd4bbd96810f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754899"
---
# <a name="ltwsdlimportergt"></a>&lt;wsdlImporter&gt;
Určuje všechny společnosti importers WSDL, která importuje metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad.  
  
\<system.ServiceModel>  
\<klient >  
\<metadata >  
\<wsdlImporters >  
\<wsdlImporter >  
  
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
|`type`|Typ tohoto elementu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<wsdlImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Určuje všechny společnosti importers WSDL, která importuje metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad.|  
  
## <a name="remarks"></a>Poznámky  
 Import metadat a také převést tento informace do různých tříd, které představují kontraktu a informace o koncovém se používá – Importér WSDL. Selektivně ji můžete importovat informace o kontraktu a koncový bod a vlastnosti, které vystavit všechny chyby při importu a přijímat informace o typu relevantní pro proces importu a převod. Také podporuje import informace o vazbě a vlastnosti, které poskytují přístup na všechny dokumenty zásad, WSDL dokumenty, rozšíření WSDL a dokumentech schémat XML.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
