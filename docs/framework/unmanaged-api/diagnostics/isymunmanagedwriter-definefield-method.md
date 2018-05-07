---
title: ISymUnmanagedWriter::DefineField – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d5b3c60845fce39ce7f904c6871e7feb16e8970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterdefinefield-method"></a>ISymUnmanagedWriter::DefineField – metoda
Definuje samostatná proměnná, která není v rámci metody. Tato metoda je použít u některých polí v třídách, bitových polí a tak dále.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [v] Metadata typ nebo metoda tokenu.  
  
 `name`  
 [v] Název pole.  
  
 `attributes`  
 [v] Atributy pole.  
  
 `cSig`  
 [v] A `ULONG32` to znamená velikost vyrovnávací paměti musí obsahovat pole podpis znakům.  
  
 `signature`  
 [v] Pole podpisy pole.  
  
 `addrKind`  
 [v] Typ adresy.  
  
 `addr1`  
 [v] První adresa pro specifikaci pole.  
  
 `addr2`  
 [v] Druhý adresa pro specifikaci pole.  
  
 `addr3`  
 [v] Je třetí adresa pro specifikaci pole.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
