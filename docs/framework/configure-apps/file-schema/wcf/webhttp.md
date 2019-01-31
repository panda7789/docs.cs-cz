---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: ca6d401109d14ce11dcd40c393cd079170e4d20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259864"
---
# <a name="webhttp"></a>\<webHttp>
Tento prvek určuje, <xref:System.ServiceModel.Description.WebHttpBehavior> koncového bodu prostřednictvím konfigurace. Toto chování při použití ve spojení s [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standardní vazbu, umožňuje programovacího modelu webové služby Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<webHttp>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Pokud je tato vlastnost nastavena na `true`, určuje nejvhodnější formát infrastruktura WCF. Automatický výběr formátu je zakázané ve výchozím nastavení pro zpětnou kompatibilitu. Automatický výběr formátu je možné povolit programově nebo prostřednictvím konfigurace.|  
|defaultBodyStyle|Určuje výchozí styl textu vrácených zpráv. Další informace najdete v tématu <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Určuje výchozí formát odchozích odpovědi pro zprávy. Další informace najdete v tématu [WCF Web HTTP formátování](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Získá nebo nastaví příznak určující, zda FaultException se vygeneruje, když vnitřní chybě serveru (stavový kód HTTP: 500) nastane.|  
|helpEnabled|Získá nebo nastaví hodnotu, která určuje, zda je povoleno na stránce nápovědy.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje sadu chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Integrace jazyka AJAX a podpora JSON](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
