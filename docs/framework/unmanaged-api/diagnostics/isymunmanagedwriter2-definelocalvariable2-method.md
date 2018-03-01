---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 – metoda
V aktuálním oboru lexikální definuje jednu proměnnou. Tuto metodu lze volat vícekrát proměnné se stejným názvem, který má více domácnostech v rámci oboru. V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [v] Místní název proměnné.  
  
 `attributes`  
 [v] Místní proměnné atributy.  
  
 `sigToken`  
 [v] Podpis tokenu metadat.  
  
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
 **Záhlaví:** CorSym.idl  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
