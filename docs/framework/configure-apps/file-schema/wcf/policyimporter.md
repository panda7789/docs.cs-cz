---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 22d90ff9d0cd5325300cf42437836f075cbf8c31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148484"
---
# <a name="ltpolicyimportergt"></a>&lt;policyImporter&gt;
Určuje programu pro import zásady, které řídí import kontrolních výrazů vlastních zásad o vazbách.  
  
 \<system.ServiceModel>  
\<klient >  
\<metadata >  
\<policyImporters >  
\<policyImporter >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`type`|Typ tohoto prvku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Určuje všechny nástroje pro import, které řídí import kontrolních výrazů vlastních zásad o vazbách.|  
  
## <a name="remarks"></a>Poznámky  
 Import zásady se používá k hledání kontrolních výrazů vlastních zásad o vazbách funkce, jakož i připojit vlastní prvek vazby, který implementuje funkce, které vyžaduje kontrolního výrazu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
