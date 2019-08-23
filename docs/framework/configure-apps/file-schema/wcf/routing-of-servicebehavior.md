---
title: <routing> z <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934188"
---
# <a name="routing-of-servicebehavior"></a>\<> směrování > \<ServiceBehavior
Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.  
  
 \<system.ServiceModel>  
\<> chování  
\<serviceBehaviors>  
\<> chování  
\<> směrování  
  
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
|filterTable|Řetězec, který určuje název směrovací tabulky obsahující filtry, které mají být vyhodnoceny směrovací službou. Tato hodnota musí odpovídat `name` atributu [ \<> elementu](filtertable.md) [ \<](filtertables.md) Filter v oddílu > filterTables.|  
|routeOnHeaderOnly|Logická hodnota určující, zda filtr prohlíží text zprávy i záhlaví, nebo pouze záhlaví. Výchozí hodnota je `true`.|  
|soapProcessingEnabled|Logická hodnota, která určuje, zda by mělo dojít ke zpracování protokolu SOAP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Po přidání do konfigurace chování služby tento prvek konfigurace povolí směrování pro službu. Můžete zadat vlastní směrovací tabulku, kterou bude služba používat v tomto elementu.  
  
 Pomocí této části konfigurace můžete při změně vzoru nasazení změnit nastavení směrování průběžně. Za běhu můžete zaregistrovat vlastní směrovací rozšíření s novým nastavením směrování a služba Směrování začne používat aktualizované informace o konfiguraci pro nové zprávy a relace a zároveň může ponechává zprávy a relace v letadlech pomocí jakýchkoli pravidel. umístit při spuštění.  Díky tomu je možné v době běhu provádět v rámci služby směrování v relaci, recyklicky méně opakovanou konfiguraci směrovací služby.  
