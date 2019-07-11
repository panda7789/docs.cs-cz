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
ms.openlocfilehash: c0a273c54559e8e297e09740ba9c770ce12d72d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760580"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask – metoda
Nastaví hodnotu, která určuje typ nenamapované kódu, ve kterém se zastaví provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [in] Hodnota cordebugunmappedstop – výčet, který určuje typ nenamapované kódu, ve kterém se ladicí program zastaví provádění.  
  
 Výchozí hodnota je STOP_OTHER_UNMAPPED. Hodnota STOP_UNMANAGED je platný pouze s definiční ladění.  
  
## <a name="remarks"></a>Poznámky  
 Pokud ladicí program nalezne kompilace just-in-time (JIT), který nemá žádné odpovídající mapování pro jazyk Microsoft intermediate language (MSIL), se zastaví spuštění, pokud byl nastaven příznak určení typu nenamapované kódu; v opačném případě krokování transparentně bude pokračovat.  
  
 Pokud ladicí program nepoužívá krokovač zadejte metodu, pak jej nebude krok nutně přes nenamapované kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
