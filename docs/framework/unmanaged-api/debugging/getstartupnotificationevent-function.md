---
title: GetStartupNotificationEvent – funkce
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: fb158b35165fb229fc78169e2508679b6749752e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122954"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent – funkce
Vytvoří nebo otevře obslužnou rutinu události, která bude signalizována jakýmkoli modulem CLR (Common Language Runtime), který se načítá v zadaném cílovém procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 pro Identifikátor procesu cílového procesu, ze kterého mají být přijímána oznámení o spuštění CLR.  
  
 `phStartupEvent`  
 mimo Ukazatel na popisovač, který bude při spuštění signalizoval modulem CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně se získal popisovač události oznámení při spuštění.  
  
 E_INVALIDARG  
 `phStartupEvent` je null nebo `debuggeePID` neodkazuje na proces, který aktuálně běží.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nelze získat popisovač události oznámení při spuštění.  
  
## <a name="remarks"></a>Poznámky  
 V operačním systému Windows `debuggeePID` mapuje identifikátor procesu operačního systému.  
  
 Událost je signalizována před spuštěním jakéhokoliv spravovaného kódu modulem CLR, který signalizace událost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim. h  
  
 **Knihovna:** dbgshim. dll  
  
 **Verze .NET Framework:** 3,5 SP1
