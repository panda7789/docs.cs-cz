---
title: "ICorDebugType::EnumerateTypeParameters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4b864b2b5fd4f2a6ed03218ce6e7b6f3bf62202
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters – metoda
Získá ukazatele rozhraní k ICorDebugTypeEnum, který obsahuje <xref:System.Type> parametry třídy odkazuje tento ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 [out] Ukazatel na adresu `ICorDebugTypeEnum` obsahující parametry typu.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `EnumerateTypeParameters` Pokud je hodnota CorElementType vrácené [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) je ELEMENT_TYPE_CLASS, Typ ELEMENT_TYPE_VALUETYPE, který, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, typu ELEMENT_TYPE_BYREF, typ ELEMENT_TYPE_ PTR, nebo ELEMENT_TYPE_FNPTR. Počet parametrů a jejich pořadí, závisí na typu:  
  
-   ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který: počet parametrů typů, které jsou součástí `ICorDebugTypeEnum` , tato metoda vrátí, bude záviset na počtu formální typ parametrů pro odpovídající třídu. Například, pokud je typ `class Dict<String,int32>`, pak `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující objekty, které představují `String` a `int32` v pořadí.  
  
-   ELEMENT_TYPE_FNPTR: Počet parametrů typů, které jsou součástí `ICorDebugTypeEnum` bude jeden větší než počet argumentů přijímány funkcí. První parametr typu obsažené v `ICorDebugTypeEnum` je návratový typ funkce a následné typ parametry jsou parametry funkce.  
  
-   ELEMENT_TYPE_ARRAY ELEMENT_TYPE_SZARRAY, typu ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: jeden typ parametr bude vrácen. Pokud typ je typ pole, jako například `int32[]`,`EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující k objekt reprezentující `int32`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
