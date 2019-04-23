---
title: ISymUnmanagedWriter::DefineGlobalVariable – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66efe5ae1fe2154684d2ac6791895b7fcbe4f7b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225912"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable – metoda
Definuje jeden globální proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 [in] Ukazatel `WCHAR` , který definuje název globální proměnné.  
  
 `attributes`  
 [in] Globální proměnné atributy.  
  
 `cSig`  
 [in] A `ULONG32` , který označuje velikost ve znacích, nástroje `signature` vyrovnávací paměti.  
  
 `signature`  
 [in] Globální proměnné podpis.  
  
 `addrKind`  
 [in] Typ adresy.  
  
 `addr1`  
 [in] První adresa pro specifikaci parametru.  
  
 `addr2`  
 [in] Druhý adresa pro specifikaci parametru.  
  
 `addr3`  
 [in] Je třetí adresa pro specifikaci parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [DefineGlobalVariable2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
