---
title: ImportFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88006703ba4a491ae458868a1431be618d37252a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471196"
---
# <a name="importfile2-method"></a>ImportFile2 – metoda
Importuje nevázaného modulů a sestavení. Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor buď neexistuje na disku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Název souboru k importu.  
  
 `pszTargetName`  
 Volitelné výstupní název souboru, který slouží k přejmenování souboru, jako je propojený do sestavení.  
  
 `pAssemblyScopeIn`  
 Volitelné oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.  
  
 `fSmartImport`  
 Při hodnotě TRUE se používá importtypes –, jinak se import je nutné provést ručně.  
  
 `pImportToken`  
 Přijímá ID pro soubor nebo sestavení.  
  
 `ppAssemblyScope`  
 Přijímá [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní. Hodnota NULL, pokud soubor není sestavení.  
  
 `pdwCountOfScopes`  
 Přijímá soubory a/nebo importovat obory nenašel.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje, vrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také:
- [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
