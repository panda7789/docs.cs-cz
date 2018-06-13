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
ms.openlocfilehash: 3692471e0652a1a812b1d0cbed9e38cc32112ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404307"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent – funkce
Vytvoří nebo otevře popisovač události, který se bude dát signál při jakékoli modul common language runtime (CLR), se načítá v zadaný cílový proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `debuggeePID`  
 [v] Proces identifikátor tento cílový proces, ze kterého chcete dostávat oznámení spuštění CLR.  
  
 `phStartupEvent`  
 [out] Ukazatel na popisovač, který bude signál pomocí modulu CLR při spuštění.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Byly úspěšně načteny popisovač událost upozornění na spuštění.  
  
 E_INVALIDARG  
 `phStartupEvent` má hodnotu null nebo `debuggeePID` neodkazuje na procesu, který je aktuálně spuštěna.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nepodařilo se získat popisovač událost upozornění na spuštění.  
  
## <a name="remarks"></a>Poznámky  
 V operačním systému Windows `debuggeePID` mapuje operační systém zpracovat identifikátor.  
  
 Událost signalizace před spuštěním spravované, že je kód spuštěn pomocí modulu CLR, který signál události.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** dbgshim.h  
  
 **Knihovna:** dbgshim.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
