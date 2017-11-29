---
title: "ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d40d1799a7c1572e8213fda3a163fb9a84060f92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle – metoda
Získá odkaz na ukazatel na zadaný spravovaný objekt, který je uvolnění paměti zpracovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handle`  
 [v] Ukazatel na spravovaný objekt, který má kolekci popisovač uvolňování paměti. Tato hodnota je <xref:System.IntPtr> objektu a je možné načíst z <xref:System.Runtime.InteropServices.GCHandle> pro spravovaného objektu.  
  
 `pOutValue`  
 [out] Ukazatel na adresu ICorDebugReferenceValue objekt, který reprezentuje odkaz na zadaný spravovaného objektu.  
  
## <a name="remarks"></a>Poznámky  
 Nezaměňujte hodnota vrácená odkazu s hodnotou odkaz na kolekci paměti.  
  
 Odkaz na vrácený se chová jako normální odkaz. Při provádění kódu pokračovat po zarážku je zakázaná. Životnost cílový objekt není ovlivněn životnost hodnota odkazu.  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle` Metoda neověřuje popisovač. Proto `GetReferenceValueFromGCHandle` metoda může potenciálně dojít k poškození ladicího programu a kód laděné, pokud je předán neplatný popisovač.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
