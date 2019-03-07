---
title: ISymUnmanagedWriter2::DefineLocalVariable2 – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d336b35e91abd1b7180c2b918edeba2e1eccdbde
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499586"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 – metoda
V aktuálním oboru lexikální definuje jednu proměnnou. Tuto metodu lze volat pro proměnnou se stejným názvem, který má více domovů v rámci oboru více než jednou. V takovém případě však hodnoty `startOffset` a `endOffset` parametry se nesmí překrývat.  
  
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
  
## <a name="parameters"></a>Parametry  
 `name`  
 [in] Název místní proměnné.  
  
 `attributes`  
 [in] Místní proměnné atributy.  
  
 `sigToken`  
 [in] Metadata token podpisu.  
  
 `addrKind`  
 [in] Typ adresy.  
  
 `addr1`  
 [in] První adresa pro specifikaci parametru.  
  
 `addr2`  
 [in] Druhý adresa pro specifikaci parametru.  
  
 `addr3`  
 [in] Je třetí adresa pro specifikaci parametru.  
  
 `startOffset`  
 [in] Počáteční odsazení pro proměnnou. Tento parametr je volitelný. Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu. Pokud je nenulovou hodnotu, proměnná spadá do posuny aktuálního oboru.  
  
 `endOffset`  
 [in] Koncové odsazení pro proměnnou. Tento parametr je volitelný. Pokud je 0, tento parametr je ignorován a proměnná je definována v rámci celého rozsahu. Pokud je nenulovou hodnotu, proměnná spadá do posuny aktuálního oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
