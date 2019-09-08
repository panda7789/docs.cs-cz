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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd138d0418bb9667a86419d719bf0b95a4bb1b12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777117"
---
# <a name="importfileex-method"></a>ImportFileEx – metoda
Importuje označené sestavení nebo nevázaný modul.  
  
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
 Plně kvalifikovaný název souboru, ze kterého se má importovat.  
  
 `pszTargetName`  
 Volitelný název cílového souboru.  
  
 `fSmartImport`  
 Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.  
  
 `dwOpenFlags`  
 Příznaky, které mají být předány do [metody OpenScope –](../metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Získá ID importovaného souboru.  
  
 `ppAssemblyScope`  
 Přijímá import sestavení oboru [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) . Je nastaven na hodnotu NULL, pokud soubor není sestavení.  
  
 `pdwCountOfScopes`  
 Přijímá počet importovaných souborů a rozsahů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)
