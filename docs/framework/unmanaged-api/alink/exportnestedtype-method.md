---
title: ExportNestedType – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: fded6b95144d4088a2abc8dfcc4ef8eda331c34f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438432"
---
# <a name="exportnestedtype-method"></a>ExportNestedType – metoda
Určuje vnořené typy jako exportovatelné. [Metoda ExportType](exporttype-method.md) může také exportovat vnořené typy, ale tato metoda je rychlejší.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID sestavení, ze kterého se má exportovat  
  
 `FileToken`  
 Token souboru nebo sestavení souboru, které definuje typ, který se dá exportovat.  
  
 `TypeToken`  
 Typ tokenu typu, který se má provést export.  
  
 `ParentType`  
 Token nadřazeného typu  
  
 `pszTypename`  
 Plně kvalifikovaný název typu, který se má exportovat  
  
 `dwFlags`  
 `ComType` příznaky jako `tdPublic` nebo `tdNested`. Tato hodnota může být předána [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Přijímá token pro exportovaný typ.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
