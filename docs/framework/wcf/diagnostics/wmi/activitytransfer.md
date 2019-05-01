---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964291"
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
