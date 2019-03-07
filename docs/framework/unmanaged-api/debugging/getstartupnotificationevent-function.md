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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487325"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent – funkce
Vytvoří nebo otevře popisovač události, která bude být signalizován při libovolné CLR (CLR), který se načítá do zadaného cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [in] Zpracovat identifikátor cílového procesu, ze kterého chcete dostávat oznámení při spuštění modulu CLR.  
  
 `phStartupEvent`  
 [out] Ukazatel na popisovač, který bude signalizován pomocí modulu CLR při spuštění.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Byly úspěšně načteny popisovač události oznámení při spuštění.  
  
 E_INVALIDARG  
 `phStartupEvent` má hodnotu null nebo `debuggeePID` neodkazuje na proces, který aktuálně běží.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nepovedlo se získat popisovač události oznámení při spuštění.  
  
## <a name="remarks"></a>Poznámky  
 V operačním systému Windows `debuggeePID` mapuje na operační systém zpracovávat identifikátor.  
  
 Událost je signalizována před jakoukoli Spravované, že kód je proveden součástí CLR, který signál události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
