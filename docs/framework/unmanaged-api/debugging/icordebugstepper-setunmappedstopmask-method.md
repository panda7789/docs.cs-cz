---
title: ICorDebugStepper::SetUnmappedStopMask – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc4e51ec60c7526f36bbe4909bec91a527e0862c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask – metoda
Nastaví hodnotu, která určuje typ nenamapovaný kódu, ve kterém se zastaví provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 [v] Hodnota CorDebugUnmappedStop – výčet, který určuje typ nenamapovaný kódu, ve kterém bude zastavení ladicího programu provádění.  
  
 Výchozí hodnota je STOP_OTHER_UNMAPPED. Hodnota STOP_UNMANAGED je platný pouze s spolupráce ladění.  
  
## <a name="remarks"></a>Poznámky  
 Když ladicí program vyhledá kompilace za běhu (JIT), který nemá žádné odpovídající mapování na Microsoft (MSIL intermediate language), zastaví provádění Pokud byl nastaven příznak zadání typu nenamapovaný kódu; Krokování s transparentně pokračuje v, jinak hodnota.  
  
 Pokud ladicí program nepoužívá krokovač zadat metodu, pak jej nebude krok nutně přes nenamapovaný kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
