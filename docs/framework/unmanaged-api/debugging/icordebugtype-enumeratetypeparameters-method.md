---
title: ICorDebugType::EnumerateTypeParameters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8fa39a54437e60737aa052c495f58422bc0d3fe
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474446"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters – metoda
Získá ukazatel rozhraní icordebugtypeenum –, který obsahuje <xref:System.Type> parametry třídy odkazuje tento ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 [out] Ukazatel na adresu `ICorDebugTypeEnum` , který obsahuje parametry typu.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `EnumerateTypeParameters` Pokud vrácena hodnota corelementtype – [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) je za řetězcem ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, typ ELEMENT_TYPE_ PTR, nebo typ ELEMENT_TYPE_FNPTR. Počet parametrů a jejich pořadí závisí na typu:  
  
-   Za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE: Počet parametrů typu, které jsou součástí `ICorDebugTypeEnum` , že tato metoda vrátí hodnotu, bude záviset na počtu parametrů formální typu pro třídu odpovídající. Například, pokud je typ `class Dict<String,int32>`, pak `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` , který obsahuje objekty, které představují `String` a `int32` postupně.  
  
-   TYP ELEMENT_TYPE_FNPTR: Počet parametrů typu, které jsou součástí `ICorDebugTypeEnum` bude jeden větší než počet argumentů přijal funkce. První parametr typu obsažené v `ICorDebugTypeEnum` je návratový typ pro funkci a následné typové parametry jsou parametry funkce.  
  
-   ELEMENT_TYPE_ARRAY ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: Vrátí se jeden parametr typu. Pokud typ je typ pole, jako například `int32[]`,`EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující objekt představující `int32`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
