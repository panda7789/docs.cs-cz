---
title: '&lt;diagnostics&gt; pro aktivaci'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20b956bb58142f26fa1402f1f974b3984ed759f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a>&lt;diagnostics&gt; pro aktivaci
Nakonfiguruje [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funkce diagnostiky pro naslouchací proces.  
  
 \<system.serviceModel.activation >  
\<Diagnostika >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`performanceCountersEnabled`|Logická hodnota, která určuje, zda jsou povoleny čítače výkonu k diagnostickým účelům.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Obsahuje nastavení konfigurace pro proces naslouchání SMSvcHost.exe.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
