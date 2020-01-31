---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: 015735e1c6c3b6c146f2fca3a9bdc28baeca2f92
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792512"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a>ICorDebugProcess2::GetDesiredNGENCompilerFlags – metoda
Získá aktuální nastavení příznaku kompilátoru, které modul CLR (Common Language Runtime) používá k výběru správného předkompilovaného (nativně) image, která se má načíst do tohoto procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwFlags`  
 mimo Ukazatel na bitovou kombinaci hodnot výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) , které se používají k výběru správné předkompilované image, která se má načíst.  
  
## <a name="remarks"></a>Poznámky  
 Použijte metodu [ICorDebugProcess2:: SetDesiredNGENCompilerFlags –](icordebugprocess2-setdesiredngencompilerflags-method.md) k nastavení příznaků, které bude modul CLR používat k výběru správné předkompilované bitové kopie, která se má načíst.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
