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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cea8a322fab6ef76873e668c622ac63e3a3f2862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>ISymUnmanagedBinder2::GetReaderForFile2 – metoda
Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní, které budou číst související s modulem symboly pro ladění.  
  
 Tato metoda poskytuje rozšířené hledání pro soubor databáze (PDB) program, než [isymunmanagedbinder::getreaderforfile –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [v] Ukazatel rozhraní import metadat.  
  
 `fileName`  
 [v] Ukazatel na název souboru.  
  
 `searchPath`  
 [v] Ukazatel na cestě pro vyhledávání.  
  
 `searchPolicy`  
 [v] Hodnota [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) výčet, který určuje zásady, který se má použít při vyhledávání pro čtečku symbol.  
  
 `pRetVal`  
 [out] Ukazatele, který je nastavený s vráceným <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Poznámky  
 Tato verze metody můžete vyhledat soubor PDB v oblastech než vpravo vedle modulu. Zásady vyhledávání lze řídit tím, že zkombinujete [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Například `AllowReferencePathAccess | AllowSymbolServerAccess` hledá PDB vedle spustitelný soubor a na serveru symbol, ale není v registru nebo použijte cestu ve spustitelném souboru. Pokud `searchPath` je zadán parametr, budou se vyhledávat vždy těchto adresářů.  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [GetReaderForFile – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
