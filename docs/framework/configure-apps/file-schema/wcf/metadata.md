---
title: '&lt;metadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06444f30ab06f04644a7a6c5ad596388ecceeaf1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmetadatagt"></a>&lt;metadata&gt;
Určuje, jak může být zpracována metadata služby.  
  
 \<systém. ServiceModel >  
\<klient >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<policyImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|Určuje všechny společnosti importers zásady, které řídí import kontrolních výrazů vlastních zásad o vazby. – Importér zásad se používá k hledání kontrolních výrazů vlastních zásad o vazbu funkce, jakož i připojit vlastní vazby element, který implementuje funkce, které vyžaduje kontrolní výraz.|  
|[\<wsdlImporters >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|Určuje všechny společnosti importers WSDL, které importovat metadata webové služby popis Language (WSDL) 1.1 s přílohami WS-zásad. Import metadat a také převést tento informace do různých tříd, které představují kontraktu a informace o koncovém se používá – Importér WSDL. Selektivně ji můžete importovat informace o kontraktu a koncový bod a vlastnosti, které vystavit všechny chyby při importu a přijímat informace o typu relevantní pro proces importu a převod. Také podporuje import informace o vazbě a vlastnosti, které poskytují přístup na všechny dokumenty zásad, WSDL dokumenty, rozšíření WSDL a dokumentech schémat XML.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<klient >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Oddíl klienta definuje seznam koncových bodů, které klient může připojit k.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [Konfigurace klienta WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [Klienti](../../../../../docs/framework/wcf/feature-details/clients.md)
