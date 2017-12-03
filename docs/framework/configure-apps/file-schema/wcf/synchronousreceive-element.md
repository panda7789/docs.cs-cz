---
title: Element &lt;synchronousReceive&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 79d78517b62e4476106ff1ed7978c770a17caf2a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsynchronousreceivegt-element"></a>Element &lt;synchronousReceive&gt;
Tento element konfigurace slouží k určení chování pro příjem zpráv v aplikaci služby nebo klienta. Nástroj nemá žádné atributy nebo podřízené elementy.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<synchronousReceive >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování koncového bodu.|  
  
## <a name="remarks"></a>Poznámky  
 Naslouchací proces kanálu nástroje použijte synchronního přijímat spíše než výchozí, asynchronní použitím toto chování. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]vydá nové vlákno čerpadlo pro každý přijatý kanál. Pokud je celá řada kanály, existuje možnost spuštění z vláken.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
