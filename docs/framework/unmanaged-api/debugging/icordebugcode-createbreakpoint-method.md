---
title: ICorDebugCode::CreateBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: b02fb0a18bfbc2e93ec204706ca1f17dde5d8c8a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125702"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint – metoda
Vytvoří zarážku v tomto segmentu kódu na zadaném posunu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `offset`  
 pro Posun, ve kterém má být vytvořena zarážka.  
  
 `ppBreakpoint`  
 mimo Ukazatel na adresu objektu "ICorDebugFunctionBreakpoint", který představuje zarážku.  
  
## <a name="remarks"></a>Poznámky  
 Předtím, než je zarážka aktivní, je nutné ji přidat do objektu procesu.  
  
 Pokud je tento kód kódem jazyka MSIL (Microsoft Intermediate Language) a existuje nativní verze kódu kompilována za běhu (JIT), zarážka bude použita také v kódu kompilovaném JIT. (Totéž platí, pokud je kód zkompilován kompilátorem JIT později.)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
