---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749592"
---
# <a name="ltbackuplistsgt"></a>&lt;backupLists&gt;
Představuje konfigurační oddíl pro definování sady zálohování služby použité při zpracování chyb. Každý podřízený element je zálohování seznam, který se zobrazí sada koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný. Pokud první koncový bod v seznamu je vypnutý, směrovací služby bude automaticky selhání na další stránku v seznamu.  To vám dává rychlý způsob, jak přidat spolehlivost k vaší aplikaci bez nutnosti naučit klientskou aplikaci, jak bude zpracováván komplexní vzory nebo všech služeb, kde jsou nasazeny.  
  
 \<system.serviceModel>  
\<směrování >  
\<backupLists >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtr >](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|Obsahuje seznam koncových bodů, které byste chtěli směrovací služby používat v případě, že primární koncový bod není dostupný. .|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Představuje konfigurační oddíl pro definování sady směrování filtrů, které určují typ služby Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> použije při vyhodnocení příchozí zprávy, jakož i směrování tabulky definující cílové koncové body k Pokud filtr odpovídá odesílat zprávy.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
