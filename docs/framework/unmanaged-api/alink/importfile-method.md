---
title: ImportFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
ms.openlocfilehash: cda6d90865f8ad2b9d565f6a6378c35b03c65bf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446989"
---
# <a name="importfile-method"></a>ImportFile – metoda
Importuje sestavení a nevázané moduly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Plně kvalifikovaný název souboru, který se má importovat  
  
 `pszTargetName`  
 Volitelný název výstupního souboru, který lze použít k přejmenování souboru, protože je propojen do sestavení.  
  
 `fSmartImport`  
 Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.  
  
 `pImportToken`  
 Ukazatel na token, kde bude uložen jedinečný identifikátor souboru. Soubor může být sestavením nebo souborem.  
  
 `ppAssemblyScope`  
 Přijme ukazatel na [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md). Pokud soubor není sestavením, může mít hodnotu NULL.  
  
 `pdwCountOfScopes`  
 Ukazatel na počet souborů nebo rozsahů, které byly naimportovány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h  
  
## <a name="see-also"></a>Viz také:

- [IALink – rozhraní](ialink-interface.md)
- [IALink2 – rozhraní](ialink2-interface.md)
- [Rozhraní API ALink](index.md)
