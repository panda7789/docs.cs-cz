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
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
