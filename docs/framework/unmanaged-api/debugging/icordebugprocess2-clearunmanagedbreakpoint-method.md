---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: 8377ead42c752d8ebe9813d9e00662b94339f8a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137247"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint – metoda
Odebere dříve nastavenou zarážku na dané adrese.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro Hodnota `CORDB_ADDRESS` určující adresu, na které byla zarážka nastavena.  
  
## <a name="remarks"></a>Poznámky  
 Zadaná zarážka by byla dříve nastavena starším voláním metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Metodu `ClearUnmanagedBreakpoint` lze volat, pokud je spuštěn proces ladění.  
  
 Metoda `ClearUnmanagedBreakpoint` vrátí kód chyby, pokud je ladicí program připojen v režimu pouze spravovaném, nebo pokud na zadané adrese neexistuje žádná zarážka.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
