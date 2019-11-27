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
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438290"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a>ISymUnmanagedWriter2::DefineLocalVariable2 – metoda
Definuje jednu proměnnou v aktuálním lexikálním oboru. Tuto metodu lze volat vícekrát pro proměnnou se stejným názvem, který má více obydlí v celém rozsahu. V takovém případě se ale hodnoty parametrů `startOffset` a `endOffset` nesmí překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Název místní proměnné.  
  
 `attributes`  
 pro Atributy místních proměnných.  
  
 `sigToken`  
 pro Token metadat podpisu  
  
 `addrKind`  
 pro Typ adresy.  
  
 `addr1`  
 pro První adresa specifikace parametru.  
  
 `addr2`  
 pro Druhá adresa specifikace parametru.  
  
 `addr3`  
 pro Třetí adresa specifikace parametru.  
  
 `startOffset`  
 pro Počáteční posun pro proměnnou Tento parametr je volitelný. Pokud je 0, tento parametr je ignorován a proměnná je definována v celém rozsahu. Pokud je to nenulová hodnota, proměnná spadá do posunu aktuálního oboru.  
  
 `endOffset`  
 pro Koncový posun proměnné Tento parametr je volitelný. Pokud je 0, tento parametr je ignorován a proměnná je definována v celém rozsahu. Pokud je to nenulová hodnota, proměnná spadá do posunu aktuálního oboru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
