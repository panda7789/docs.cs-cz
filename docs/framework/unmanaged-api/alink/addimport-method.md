---
title: AddImport – metoda
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 52e52ac62e2dcfeb182da3014a863409f640274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446652"
---
# <a name="addimport-method"></a>AddImport – metoda
Přidá importy do sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Jedinečné ID sestavení, které se má rozšířit  
  
 `ImportToken`  
 Jedinečné ID, které bylo načteno z [metody importFile –](importfile-method.md)souboru, který má být importován.  
  
 `dwFlags`  
 Značky COM+ FileDef, například `ffContainsNoMetaData` a `ffWriteable`. `dwFlags` se předává do [metody DefineFile –](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Ukazatel na token, který obdrží ID pro výsledný soubor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
