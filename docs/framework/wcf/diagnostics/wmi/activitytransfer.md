---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662813"
---
# <a name="activitytransfer"></a>ActivityTransfer
Aktivita událost přenosu  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ActivityTransfer nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ActivityTransfer má následující vlastnosti:  
  
### <a name="activityid"></a>ID aktivity  
  
- Datový typ: objekt  
    Typ přístupu: jen pro čtení  
  
- ID aktivity  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- Datový typ: objekt  
    Typ přístupu: jen pro čtení  
  
- ID související aktivity  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel.|
