---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940494"
---
# <a name="webhttp"></a>\<webHttp>
Tento prvek určuje <xref:System.ServiceModel.Description.WebHttpBehavior> u koncového bodu prostřednictvím konfigurace. Toto chování, při použití ve spojení s [ \<WebHttpBinding >](webhttpbinding.md) standardní vazbou, povoluje webový programovací model pro službu Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
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
|automaticFormatSelectionEnabled|Pokud je tato vlastnost nastavena na `true`hodnotu, infrastruktura WCF určí nejvhodnější formát, který se má použít. Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility. Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace.|  
|defaultBodyStyle|Určuje výchozí styl textu vrácených zpráv. Další informace najdete v tématech <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Určuje výchozí formát odchozí odpovědi pro zprávy. Další informace najdete v tématu [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Získá nebo nastaví příznak určující, zda je FaultException generována při vnitřní chybě serveru (kód stavu HTTP: 500) dojde k chybě.|  
|helpEnabled|Získává nebo nastavuje hodnotu, která určuje, jestli je povolená stránka pro usnadnění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje sadu chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Integrace jazyka AJAX a podpora JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
