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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f38f9a3ebd88e0a5abb7a6bc8cb4026dc7d0f068
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736934"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda
Získá odkaz na ukazatel na zadaný spravovaný objekt, který má uvolňování paměti zpracovávají.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `handle`  
 [in] Ukazatel na spravovaný objekt, který má popisovač kolekce uvolnění paměti. Tato hodnota je <xref:System.IntPtr> objektu a je možné načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaný objekt.  
  
 `pOutValue`  
 [out] Ukazatel na adresu icordebugreferencevalue – objekt, který představuje odkaz na zadaný spravovaný objekt.  
  
## <a name="remarks"></a>Poznámky  
 Nezaměňujte hodnotu vráceného odkazu s hodnotou odkaz kolekce uvolnění paměti.  
  
 Vrácený odkaz se chová jako normální odkaz. Při provádění kódu pokračuje po zarážku je zakázaný. Životnost cílový objekt nemá vliv životnost hodnota odkazu.  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle` Popisovač metody nelze ověřit. Proto `GetReferenceValueFromGCHandle` metoda může potenciálně poškodit ladicího programu a kódu, který se právě ladí, pokud je předán neplatný popisovač.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
