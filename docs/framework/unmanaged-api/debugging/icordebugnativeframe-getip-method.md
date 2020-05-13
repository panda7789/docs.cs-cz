---
title: ICorDebugNativeFrame::GetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 53576ca938074fb7e5974a96bb53a84cb6ed67ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213592"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP – metoda
Získá umístění posunutí nativního kódu, na který je aktuálně nastaven ukazatel na instrukci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pnOffset`  
 mimo Ukazatel na umístění posunu v nativním kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je aktivní rámec zásobníku, který je reprezentován tímto "ICorDebugNativeFrame", posunem je adresa dalšího pokynu, který má být proveden. Pokud tento rámec zásobníku není aktivní, posun je adresa další instrukce, která se má provést, když se znovu aktivuje rámec zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
