---
title: "ISymUnmanagedBinder::GetReaderForFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderForFile
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c50bb4ca36043fc2491c9a0615b682c94c422e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>ISymUnmanagedBinder::GetReaderForFile – metoda
Vrátí zadaný metadat rozhraní a název souboru správný <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, která budou číst související s modulem symboly pro ladění.  
  
 Tato metoda se otevřít soubor databáze (PDB) program pouze v případě, že je vedle spustitelný soubor. Tato změna byla provedená z bezpečnostních důvodů. Pokud potřebujete rozsáhlejší vyhledejte soubor PDB, použijte [isymunmanagedbinder2::getreaderforfile2 –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [v] Ukazatel rozhraní import metadat.  
  
 `fileName`  
 [v] Ukazatel na název souboru.  
  
 `searchPath`  
 [v] Ukazatel na cestě pro vyhledávání.  
  
 `pRetVal`  
 [out] Ukazatele, který je nastavený s vráceným <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [GetReaderForFile2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
