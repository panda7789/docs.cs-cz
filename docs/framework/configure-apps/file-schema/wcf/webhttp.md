---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399164"
---
# \<webHttp>
Tento prvek určuje <xref:System.ServiceModel.Description.WebHttpBehavior> u koncového bodu prostřednictvím konfigurace. Toto chování, při použití ve spojení se [\<webHttpBinding>](webhttpbinding.md) standardní vazbou, umožňuje model webového programování pro službu Windows Communication Foundation (WCF).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Pokud je tato vlastnost nastavena na hodnotu `true` , infrastruktura WCF určí nejvhodnější formát, který se má použít. Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility. Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace.|  
|defaultBodyStyle|Určuje výchozí styl textu vrácených zpráv. Další informace najdete v tématech <xref:System.ServiceModel.Web.WebMessageBodyStyle> a [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Určuje výchozí formát odchozí odpovědi pro zprávy. Další informace najdete v tématu [formátování webového HTTP WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|Třída FaultExceptionEnabled|Získá nebo nastaví příznak určující, zda je FaultException generována v případě, že dojde k vnitřní chybě serveru (kód stavu HTTP: 500).|  
|helpEnabled|Získává nebo nastavuje hodnotu, která určuje, jestli je povolená stránka pro usnadnění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje sadu chování koncového bodu.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Integrace jazyka AJAX a podpora JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
