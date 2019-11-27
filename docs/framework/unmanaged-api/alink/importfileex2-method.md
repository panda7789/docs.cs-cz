---
title: ImportFileEx2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 7e270dbfc63c03e77cb4b0694296e48c2035b8a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445687"
---
# <a name="importfileex2-method"></a>ImportFileEx2 – metoda
Importuje sestavení a nevázané moduly. Tato metoda se podobá [metodě importFile –](importfile-method.md), ale funguje i v případě, že soubor, který importujete, na disku neexistuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFilename`  
 Název souboru, který se má importovat  
  
 `pszTargetName`  
 Volitelný název cílového souboru.  
  
 `pAssemblyScopeIn`  
 Volitelné rozhraní importu oboru rozhraní [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .  
  
 `fSmartImport`  
 Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.  
  
 `dwOpenFlags`  
 Příznaky, které mají být předány do [metody OpenScope –](../metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Získá jedinečné ID pro sestavení nebo soubor.  
  
 `ppAssemblyScope`  
 Přijímá import sestavení oboru [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . Pokud soubor není sestavením, může mít hodnotu NULL.  
  
 `pdwCountOfScopes`  
 Přijímá počet importovaných souborů a oborů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)
