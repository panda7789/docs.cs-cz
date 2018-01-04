---
title: '&lt;webHttp&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b488d4e4884f92b107b2b6be71827a2f8b4cdbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebhttpgt"></a>&lt;webHttp&gt;
Určuje tento element <xref:System.ServiceModel.Description.WebHttpBehavior> v koncovém bodě prostřednictvím konfigurace. Toto chování, pokud se používá ve spojení s [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazby umožňuje programovací model webových pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<webHttp >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttp />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Pokud je tato vlastnost nastavená na `true`, určuje nejlepší formát pro infrastrukturu WCF. Automatický výběr formátu ve výchozím nastavení vypnutá pro zpětné kompatibility. Automatický výběr formátu lze povolit prostřednictvím kódu programu, nebo prostřednictvím konfigurace.|  
|defaultBodyStyle|Určuje výchozí styl textu vrácené zprávy. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Web.WebMessageBodyStyle> a [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Určuje výchozí formát odchozí odpovědi pro zprávy. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Získá nebo nastaví příznak, který určuje, zda FaultException se vygeneruje, když se o vnitřní chybu serveru (kód stavu HTTP: 500) dojde k.|  
|helpEnabled|Získá nebo nastaví hodnotu, která určuje, zda je povoleno na stránce nápovědy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje sadu chování koncový bod.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Integrace jazyka AJAX a podpora JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [\<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
