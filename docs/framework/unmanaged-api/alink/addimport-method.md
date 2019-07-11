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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31dec878c92e2e2196ab2d586a78578b7244a41a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742238"
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
 Jedinečné ID sestavení potřeba rozšířit.  
  
 `ImportToken`  
 Jedinečné ID získaných [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), souboru k importu.  
  
 `dwFlags`  
 COM + FileDef označí jako `ffContainsNoMetaData` a `ffWriteable`. `dwFlags` je předán [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Ukazatel na token, který přijímá ID pro výsledný soubor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje, vrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
