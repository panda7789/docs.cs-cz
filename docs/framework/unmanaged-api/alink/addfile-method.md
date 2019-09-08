---
title: AddFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1406c68f1f6abff4d140b131f5f630d0fd767e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787684"
---
# <a name="addfile-method"></a>AddFile – metoda
Přidá soubory do sestavení. Lze také použít k vytvoření nevázaných modulů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Jedinečné ID sestavení, které se má rozšířit  
  
 `pszFilename`  
 Plně kvalifikovaný název souboru, který se má přidat  
  
 `dwFlags`  
 Značky `ffContainsNoMetaData` modelu COM+ FileDef jako a `ffWriteable`. `dwFlags`je předán [metodě DefineFile –](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Rozhraní [rozhraní IMetaDataEmit](../metadata/imetadataemit-interface.md) , které se v případě potřeby používá k vygenerování metadat.  
  
 `pFileToken`  
 Ukazatel na místo, kde bude uloženo jedinečné ID přidaného souboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
