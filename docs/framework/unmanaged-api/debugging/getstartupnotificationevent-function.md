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
ms.openlocfilehash: 3377dcd5d45ca8e31a57a75bd81366d41837c12c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860712"
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
 `phStartupEvent`má hodnotu null `debuggeePID` nebo neodkazuje na proces, který aktuálně běží.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nelze získat popisovač události oznámení při spuštění.  
  
## <a name="remarks"></a>Poznámky  
 V operačním systému Windows se `debuggeePID` mapuje na identifikátor procesu operačního systému.  
  
 Událost je signalizována před spuštěním jakéhokoliv spravovaného kódu modulem CLR, který signalizace událost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim. h  
  
 **Knihovna:** dbgshim. dll  
  
 **Verze .NET Framework:** 3,5 SP1
