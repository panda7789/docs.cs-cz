---
title: ICorDebugFunction::GetILCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: c2ce4b95de75bef3928e144656b565676568caa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137902"
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode – metoda
Získá instanci ICorDebugCode, která představuje kód jazyka MSIL (Microsoft Intermediate Language) přidružený k tomuto objektu ICorDebugFunction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppCode`  
 mimo Ukazatel na instanci `ICorDebugCode` nebo hodnotu null, pokud funkce nebyla zkompilována do jazyka MSIL.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je u této funkce povolená možnost upravit a pokračovat, metoda `GetILCode` získá kód jazyka MSIL odpovídající upravované verzi kódu této funkce v modulu CLR (Common Language Runtime).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
