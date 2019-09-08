---
title: AddFile2 – metoda
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3a6892dbed172c0be3b036014d393657dbc8593
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777517"
---
# <a name="addfile2-method"></a>AddFile2 – metoda
Přidá soubory do sestavení. Lze také použít k vytvoření nevázaných modulů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 ID pro sestavení, ke kterému je soubor přidán.  
  
 `pszFilename`  
 Název souboru, který se má přidat  
  
 `dwFlags`  
 Příznaky `FileDef` modelu COM+, `ffContainsNoMetaData` například `ffWriteable`a. `dwFlags`je předán [metodě DefineFile –](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Rozhraní k rozhraní [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) .  
  
 `pFileToken`  
 Získá ID přidávaného souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)
