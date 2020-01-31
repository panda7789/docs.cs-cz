---
title: ICorDebugNativeFrame::CanSetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792806"
---
# <a name="icordebugnativeframecansetip-method"></a>ICorDebugNativeFrame::CanSetIP – metoda
Získá hodnotu HRESULT, která označuje, zda je bezpečné nastavit ukazatel na instrukce (IP) na zadané umístění posunu v nativním kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nOffset`  
 pro Požadované nastavení pro ukazatel na instrukci.  
  
## <a name="remarks"></a>Poznámky  
 Použijte metodu `CanSetIP` před voláním metody [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) . Pokud `CanSetIP` vrátí jakýkoli HRESULT jiný než S_OK, můžete přesto vyvolat `ICorDebugNativeFrame::SetIP`, ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správném spuštění kódu, který je právě laděn.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
