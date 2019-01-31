---
title: <routing> z <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 3f23cbb45aa72b1aae18c845e68b426a4214d499
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261773"
---
# <a name="routing-of-servicebehavior"></a>\<směrování > z \<serviceBehavior >
Poskytuje přístup ke službě Směrování a povolit dynamickou změnu konfigurace směrování.  
  
 \<system.ServiceModel>  
\<chování >  
\<serviceBehaviors>  
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
|filterTable|Řetězec určující název směrovací tabulku, která obsahuje filtry, který se má vyhodnotit ve službě Směrování. Tato hodnota musí odpovídat `name` atribut [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) prvek [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) části.|  
|routeOnHeaderOnly|Logická hodnota, která určuje, zda bude text zprávy a záhlaví nebo pouze záhlaví prozkoumat filtr. Výchozí hodnota je `true`.|  
|soapProcessingEnabled|Logická hodnota určující, zda by měla probíhat zpracování SOAP.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Když se přidá do konfigurace chování služby, umožňuje tento prvek konfigurace, směrování pro službu. Můžete určit skutečný směrovací tabulky používané služby v tomto elementu.  
  
 Používá tento konfigurační oddíl, můžete změnit nastavení směrování v reálném čase při změně vzorek vašeho nasazení. Za běhu zaregistrujete vlastní rozšíření směrování s novými nastaveními směrování a služba Směrování se začít používat informace o aktualizovanou konfiguraci pro nové zprávy a relací, ale zároveň je nechává vydávaných za pochodu zpráv/relací pomocí určit jakákoli pravidla byly v místo při jejich spuštění.  Získáte možnost provádět relace typově bezpečný, recyklace bez změny konfigurace směrování služby za běhu.  
  
