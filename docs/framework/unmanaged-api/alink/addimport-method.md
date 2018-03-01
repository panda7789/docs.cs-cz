---
title: "Addimport – Method1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a>Addimport – Method1
Přidá importy sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Jedinečné ID sestavení, které má být rozšířen.  
  
 `ImportToken`  
 Jedinečné ID načítají [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), souboru určených k importu.  
  
 `dwFlags`  
 Modelu COM + FileDef flags – například `ffContainsNoMetaData` a `ffWriteable`. `dwFlags`Předaný [definefile – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Ukazatel na token, který přijímá ID pro výsledný soubor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h  
  
## <a name="see-also"></a>Viz také  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
