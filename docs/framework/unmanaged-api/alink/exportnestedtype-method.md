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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777273"
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
 `ComType`příznaky jako `tdPublic` nebo `tdNested`. Tato hodnota může být předána [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Přijímá token pro exportovaný typ.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
