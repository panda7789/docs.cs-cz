---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída třídy ServiceThrottlingBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída třídy ServiceThrottlingBehavior má následující vlastnosti:  
  
### <a name="maxconcurrentcalls"></a>maxConcurrentCalls  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet zpráv ve všech objektech dispečera v ServiceHost aktivně zpracovávají.  
  
### <a name="maxconcurrentinstances"></a>maxConcurrentInstances  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet objekty služby, které mohou být prováděny současně.  
  
### <a name="maxconcurrentsessions"></a>maxConcurrentSessions  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet relací, které hostitele může přijmout najednou.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
