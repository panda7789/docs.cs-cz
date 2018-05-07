---
title: SetAssemblyFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ade568889d1c0203115f160d855de8c598798196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2 – metoda
Nastaví název a možnosti pro nové sestavení. Tato metoda není volána při vytvoření nepřipojeného moduly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFilename`  
 Název souboru manifestu.  
  
 `pEmitter`  
 [Imetadataemit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) rozhraní pro tento soubor.  
  
 `afFlags`  
 Možnosti reprezentována [AssemblyFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Získá jedinečné ID pro sestavení vytvářen.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
