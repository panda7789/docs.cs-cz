---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 47647bf0460507b4c88b47bf87bfcc3bf620aecc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137212"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda
Získá ukazatel odkazu na zadaný spravovaný objekt, který má popisovač uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `handle`  
 pro Ukazatel na spravovaný objekt, který má popisovač uvolňování paměti. Tato hodnota je objekt <xref:System.IntPtr> a lze ho načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaný objekt.  
  
 `pOutValue`  
 mimo Ukazatel na adresu objektu ICorDebugReferenceValue, který představuje odkaz na zadaný spravovaný objekt.  
  
## <a name="remarks"></a>Poznámky  
 Nepleťte si vrácenou referenční hodnotu s referenční hodnotou uvolňování paměti.  
  
 Vrácený odkaz se chová jako normální reference. Je zakázáno, pokud provádění kódu pokračuje po zarážce. Doba života cílového objektu není ovlivněna životností referenční hodnoty.  
  
> [!NOTE]
> Metoda `GetReferenceValueFromGCHandle` neověřuje popisovač. Proto metoda `GetReferenceValueFromGCHandle` může potenciálně poškodit ladicí program i kód, který je laděn, pokud je předán neplatný popisovač.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
