---
title: "&lt;routing&gt; – &lt;serviceBehavior&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15e46f8d9550d4361ef92c1fa4860f17a2dfd088
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;routing&gt; – &lt;serviceBehavior&gt;
Poskytuje běhové přístup ke službě Směrování a povolit dynamické změnu konfigurace směrování.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<směrování >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String" 
               routeOnHeadersOnly="Boolean" 
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|filterTable|Řetězec, který určuje název směrovací tabulka, která obsahuje filtry k vyhodnocení pomocí služby směrování. Tato hodnota musí odpovídat `name` atribut [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element v [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) části.|  
|routeOnHeaderOnly|Logická hodnota, která určuje, zda bude text zprávy a záhlaví nebo pouze záhlaví zkontrolujte filtru. Výchozí hodnota je `true`.|  
|soapProcessingEnabled|Logická hodnota, která určuje, zda má vzniknout zpracování protokolu SOAP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Při přidání do konfigurace chování služby, tento element konfigurace umožňuje směrování pro službu. Můžete zadat skutečný směrovací tabulky pro použití službou v tomto elementu.  
  
 Pomocí tento konfigurační oddíl, můžete změnit nastavení směrování za chodu při změně vzor vaše nasazení. V době běhu směrování rozšíření můžete zaregistrovat pomocí nového nastavení směrování a služba Směrování začne, pomocí informací o aktualizovanou konfiguraci nových zpráv a relace, a nechat neukládají zprávy nebo relací pomocí ať pravidla byly v místní při jejich spuštění.  To vám umožňuje provést bezpečné relace, recyklaci bez změny konfigurace služby směrování za běhu.  
  
