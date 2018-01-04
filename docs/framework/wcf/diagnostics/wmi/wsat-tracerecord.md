---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24f74d4086a5499d3bfd4ef6183d377528acc21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída WSAT_TraceRecord nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída WSAT_TraceRecord má následující vlastnosti:  
  
### <a name="activityid"></a>ID aktivity  
 Datový typ: objekt  
Přístup k typu: jen pro čtení  
  
 ID aktivity záznamu trasování.  
  
### <a name="eventid"></a>ID události  
 Datový typ: sint32  
Přístup k typu: jen pro čtení  
  
 Událost s ID záznamu trasování.  
  
### <a name="tracerecord"></a>TraceRecord  
 Datový typ: řetězec  
Přístup k typu: jen pro čtení  
  
 Záznam trasování  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
