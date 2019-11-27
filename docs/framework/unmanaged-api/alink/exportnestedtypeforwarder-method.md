---
title: ExportNestedTypeForwarder – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: cc81ccd1c754e3d34c54737f4560b4f81d5cc916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438411"
---
# <a name="exportnestedtypeforwarder-method"></a>ExportNestedTypeForwarder – metoda
Přidá předávaného typu pro vnořený typ do tabulky typů daného sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
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
 Token souboru nebo ID sestavení souboru, který definuje typ.  
  
 `TypeToken`  
 Token pro typ  
  
 `ParentType`  
 Token nadřazeného typu  
  
 `pszTypename`  
 Plně kvalifikovaný název typu, který se má exportovat  
  
 `dwFlags`  
 `ComType` příznaky jako `tdPublic` nebo `tdNested`.  
  
 `pType`  
 Přijímá token pro typ exportu. To je nezbytné jenom pro vygenerování vnořených typů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
