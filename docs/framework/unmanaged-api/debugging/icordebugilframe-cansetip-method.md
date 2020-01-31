---
title: ICorDebugILFrame::CanSetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788596"
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP – metoda
Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 pro Požadované nastavení pro ukazatel na instrukci.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) použijte metodu `CanSetIP`. Pokud `CanSetIP` vrátí jakýkoli HRESULT jiný než S_OK, můžete přesto vyvolat `ICorDebugILFrame::SetIP`, ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správném spuštění kódu, který je právě laděn.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug, h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
