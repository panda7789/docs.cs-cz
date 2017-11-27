---
title: "ISymUnmanagedWriter::DefineLocalVariable – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineLocalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e454aa2c2dd8ceb8f8dbbc03bdd1e70e8a800de2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable – metoda
V aktuálním oboru lexikální definuje jednu proměnnou. Tuto metodu lze volat vícekrát proměnné se stejným názvem, který má více domácnostech v rámci oboru. V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [v] Ukazatel na `WCHAR` , který definuje místní název proměnné.  
  
 `attributes`  
 [v] Místní proměnné atributy.  
  
 `cSig`  
 [v] A `ULONG32` určující velikost v bajtech z `signature` vyrovnávací paměti.  
  
 `signature`  
 [v] Místní proměnné podpis.  
  
 `addrKind`  
 [v] Typ adresy.  
  
 `addr1`  
 [v] První adresa pro specifikaci parametru.  
  
 `addr2`  
 [v] Druhý adresu pro specifikaci parametru.  
  
 `addr3`  
 [v] Je třetí adresa pro specifikaci parametru.  
  
 `startOffset`  
 [v] Počáteční odsazení proměnné. Tento parametr je volitelný. Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu. Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.  
  
 `endOffset`  
 [v] Koncové posunutí pro proměnnou. Tento parametr je volitelný. Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu. Pokud je nenulovou hodnotu, proměnná spadá do posunutí aktuálního oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Defineglobalvariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [Definelocalvariable2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
