---
title: ImportFileEx – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: bee7db61beb9ed8c00cf584924be690a67d92eac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446948"
---
# <a name="importfileex-method"></a>ImportFileEx – metoda
Imports indicated assembly or unbound module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Fully qualified name of file from which to import.  
  
 `pszTargetName`  
 Optional name of target file.  
  
 `fSmartImport`  
 If TRUE, ImportTypes is used, otherwise importing must be performed manually.  
  
 `dwOpenFlags`  
 Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Receives ID of the file being imported.  
  
 `ppAssemblyScope`  
 Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface. Is set to NULL if file is not an assembly.  
  
 `pdwCountOfScopes`  
 Receives count of imported files and/or scopes.  
  
## <a name="return-value"></a>Návratová hodnota  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>Požadavky  
 Requires alink.h.  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [ALink API](index.md)
