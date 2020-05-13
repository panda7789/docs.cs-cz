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
ms.openlocfilehash: 21890f8130ec677cb88f2f5d7ef648aa19e67e71
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213059"
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
 Použijte `CanSetIP` metodu před voláním metody [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) . Pokud `CanSetIP` vrátí hodnotu HRESULT jinou než S_OK, můžete stále vyvolat `ICorDebugNativeFrame::SetIP` , ale není nijak zaručeno, že ladicí program bude pokračovat v bezpečném a správného spuštění kódu, který je laděn.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také
