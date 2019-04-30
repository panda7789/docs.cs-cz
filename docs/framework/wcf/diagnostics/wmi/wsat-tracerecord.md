---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923406"
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
Typ přístupu: jen pro čtení  
  
 ID aktivity záznamu trace.  
  
### <a name="eventid"></a>ID události  
 Datový typ: sint32  
Typ přístupu: jen pro čtení  
  
 ID události trasování záznamu.  
  
### <a name="tracerecord"></a>TraceRecord  
 Datový typ: řetězec  
Typ přístupu: jen pro čtení  
  
 Záznam trasování  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|
