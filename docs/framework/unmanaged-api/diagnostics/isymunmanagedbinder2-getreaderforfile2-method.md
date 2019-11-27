---
title: ISymUnmanagedBinder2::GetReaderForFile2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
ms.openlocfilehash: 756ba2e71ca2e3e817a0a8b89165bb807368c1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449328"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 – metoda
Vzhledem k rozhraní metadat a názvu souboru vrátí správné rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) , které přečte symboly ladění spojené s modulem.  
  
 Tato metoda poskytuje rozsáhlejší hledání souboru databáze programu (PDB) než metoda [ISymUnmanagedBinder:: GetReaderForFile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 pro Ukazatel na rozhraní pro import metadat.  
  
 `fileName`  
 pro Ukazatel na název souboru.  
  
 `searchPath`  
 pro Ukazatel na cestu pro hledání.  
  
 `searchPolicy`  
 pro Hodnota výčtu [CorSymSearchPolicyAttributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) , která určuje zásadu, která se má použít při hledání čtečky symbolů.  
  
 `pRetVal`  
 mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="remarks"></a>Poznámky  
 Tato verze metody může vyhledat soubor PDB v jiných oblastech než na pravé straně modulu. Zásady hledání je možné řídit kombinací [CorSymSearchPolicyAttributes –](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). `AllowReferencePathAccess | AllowSymbolServerAccess` například vyhledá soubor PDB vedle spustitelného souboru a na serveru symbolů, ale nedotazuje se do registru ani nepoužije cestu ve spustitelném souboru. Je-li zadán parametr `searchPath`, budou tyto adresáře vždy prohledány.  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [GetReaderForFile – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
