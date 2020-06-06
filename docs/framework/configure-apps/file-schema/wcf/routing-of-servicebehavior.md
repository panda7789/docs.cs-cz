---
title: <routing> z <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397736"
---
# <a name="routing-of-servicebehavior"></a>\<routing> z \<serviceBehavior>
Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
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
|filterTable|Řetězec, který určuje název směrovací tabulky obsahující filtry, které mají být vyhodnoceny směrovací službou. Tato hodnota musí odpovídat `name` atributu [\<filterTable>](filtertable.md) elementu v [\<filterTables>](filtertables.md) oddílu.|  
|routeOnHeaderOnly|Logická hodnota určující, zda filtr prohlíží text zprávy i záhlaví, nebo pouze záhlaví. Výchozí formát je `true`.|  
|soapProcessingEnabled|Logická hodnota, která určuje, zda by mělo dojít ke zpracování protokolu SOAP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Po přidání do konfigurace chování služby tento prvek konfigurace povolí směrování pro službu. Můžete zadat vlastní směrovací tabulku, kterou bude služba používat v tomto elementu.  
  
 Pomocí této části konfigurace můžete při změně vzoru nasazení změnit nastavení směrování průběžně. Za běhu můžete zaregistrovat vlastní směrovací rozšíření s novým nastavením směrování a služba Směrování začne používat aktualizované informace o konfiguraci pro nové zprávy a relace a zároveň zanechává zprávy a relace v letadle pomocí pravidel, která byla zahájena.  Díky tomu je možné v době běhu provádět v rámci služby směrování v relaci, recyklicky méně opakovanou konfiguraci směrovací služby.  
