---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b56c431c0e8dbab7bd4680a6e692d9b4f6e0eec4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltpolicyimportergt"></a>&lt;policyImporter&gt;
Určuje program pro import zásady, kterými se řídí import kontrolních výrazů vlastních zásad o vazby.  
  
 \<systém. ServiceModel >  
\<klient >  
\<metadata >  
\<policyImporters >  
\<policyImporter >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
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
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Určuje všechny společnosti importers zásady, které řídí import kontrolních výrazů vlastních zásad o vazby.|  
  
## <a name="remarks"></a>Poznámky  
 – Importér zásad se používá k hledání kontrolních výrazů vlastních zásad o vazbu funkce, jakož i připojit vlastní vazby element, který implementuje funkce, které vyžaduje kontrolní výraz.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
