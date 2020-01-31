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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791314"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters – metoda
Získá ukazatel rozhraní na ICorDebugTypeEnum, který obsahuje parametry <xref:System.Type> třídy, na kterou odkazuje tento ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 mimo Ukazatel na adresu `ICorDebugTypeEnum`, která obsahuje parametry typu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota CorElementType – vrácená funkcí [ICorDebugType:: GetType](icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_FNPTR, můžete použít `EnumerateTypeParameters`. Počet parametrů a jejich pořadí závisí na typu:  
  
- ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE: počet parametrů typu obsažených v `ICorDebugTypeEnum`, které tato metoda vrátí, bude záviset na počtu formálních parametrů typu pro odpovídající třídu. Například pokud je typ `class Dict<String,int32>`, `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum`, který obsahuje objekty reprezentující `String` a `int32` v sekvenci.  
  
- ELEMENT_TYPE_FNPTR: počet parametrů typu obsažených v `ICorDebugTypeEnum` bude o jeden větší než počet argumentů přijatých funkcí. První parametr typu obsažený v `ICorDebugTypeEnum` je návratový typ pro funkci a následné parametry typu jsou parametry funkce.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: vrátí se jeden parametr typu. Například pokud je typ pole typ, například `int32[]`,`EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` obsahující objekt reprezentující `int32`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
