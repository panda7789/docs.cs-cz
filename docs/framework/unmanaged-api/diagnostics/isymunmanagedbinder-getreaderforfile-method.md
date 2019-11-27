---
title: ISymUnmanagedBinder::GetReaderForFile – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: 94cda16466ea5a3d35a478a2ae80281e9414f719
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449355"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>ISymUnmanagedBinder::GetReaderForFile – metoda
Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.  
  
 Tato metoda otevře soubor programové databáze (PDB) pouze v případě, že se nachází vedle spustitelného souboru. Tato změna byla provedena z hlediska zabezpečení. Pokud potřebujete rozsáhlejší hledání souboru PDB, použijte metodu [ISymUnmanagedBinder2 –:: GetReaderForFile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 pro Ukazatel na rozhraní pro import metadat.  
  
 `fileName`  
 pro Ukazatel na název souboru.  
  
 `searchPath`  
 pro Ukazatel na cestu pro hledání.  
  
 `pRetVal`  
 mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [GetReaderForFile2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
