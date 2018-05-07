---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
