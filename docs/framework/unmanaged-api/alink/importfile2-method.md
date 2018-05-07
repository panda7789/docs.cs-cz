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
ms.openlocfilehash: 61bc7783823408164ae2b073e097a0e85e193be6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="importfile2-method"></a>ImportFile2 – metoda
Importuje sestavení a nevázaný moduly. Tato metoda je jako [importfile – metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale funguje i v případě, že importovaný soubor neexistuje na disku.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pszFilename`  
 Název soubor pro import.  
  
 `pszTargetName`  
 Název souboru volitelný výstup, který slouží k přejmenování souboru, jako je propojena do sestavení.  
  
 `pAssemblyScopeIn`  
 Volitelné oboru [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní.  
  
 `fSmartImport`  
 V případě hodnoty TRUE je používán importtypes –, jinak se import se musí provádět ručně.  
  
 `pImportToken`  
 Získá ID pro soubor nebo sestavení.  
  
 `ppAssemblyScope`  
 Přijme [imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní. Hodnota NULL, pokud soubor není sestavení.  
  
 `pdwCountOfScopes`  
 Obdrží nalezen soubory nebo obory importovat.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje alink.h.  
  
## <a name="see-also"></a>Viz také  
 [IALink – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 – rozhraní](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Rozhraní API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
