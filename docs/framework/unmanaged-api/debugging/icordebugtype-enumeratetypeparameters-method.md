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
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379995"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters – metoda
Získá ukazatel rozhraní na ICorDebugTypeEnum, který obsahuje <xref:System.Type> parametry třídy, na kterou odkazuje tento ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 mimo Ukazatel na adresu `ICorDebugTypeEnum` , která obsahuje parametry typu.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít, `EnumerateTypeParameters` Pokud hodnota CorElementType – vrácená funkcí [ICorDebugType:: GetType](icordebugtype-gettype-method.md) je ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_FNPTR. Počet parametrů a jejich pořadí závisí na typu:  
  
- ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE: počet parametrů typu obsažených v `ICorDebugTypeEnum` metodě, kterou vrací tato metoda, bude záviset na počtu formálních parametrů typu pro odpovídající třídu. Například pokud je typ `class Dict<String,int32>` , pak `EnumerateTypeParameters` vrátí objekt `ICorDebugTypeEnum` , který obsahuje objekty reprezentující `String` a `int32` v sekvenci.  
  
- ELEMENT_TYPE_FNPTR: počet parametrů typu obsažených v poli `ICorDebugTypeEnum` bude větší než počet argumentů přijatých funkcí. První parametr typu obsažený v parametru `ICorDebugTypeEnum` je návratový typ pro funkci a následné parametry typu jsou parametry funkce.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR: vrátí se jeden parametr typu. Například pokud je typ pole typu `int32[]` , například, `EnumerateTypeParameters` vrátí `ICorDebugTypeEnum` objekt, který obsahuje objekt reprezentující `int32` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
