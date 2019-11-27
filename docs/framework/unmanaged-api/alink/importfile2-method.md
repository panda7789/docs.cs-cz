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
ms.openlocfilehash: 17f158167d4075783d1aa594fb61cc9e28d30dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446980"
---
# <a name="importfile2-method"></a>ImportFile2 – metoda
Importuje sestavení a nevázané moduly. Tato metoda se podobá [metodě importFile –](importfile-method.md), ale funguje i v případě, že soubor, který importujete, na disku neexistuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 Název souboru, který se má importovat  
  
 `pszTargetName`  
 Volitelný název výstupního souboru, který lze použít k přejmenování souboru, protože je propojen do sestavení.  
  
 `pAssemblyScopeIn`  
 Volitelné rozhraní oboru [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md)  
  
 `fSmartImport`  
 Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.  
  
 `pImportToken`  
 Přijímá ID souboru nebo sestavení.  
  
 `ppAssemblyScope`  
 Přijímá rozhraní [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . Hodnota NULL, pokud soubor není sestavení.  
  
 `pdwCountOfScopes`  
 Přijímá nalezené soubory nebo obory, které byly importovány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
