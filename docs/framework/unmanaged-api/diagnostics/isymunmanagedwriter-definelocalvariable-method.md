---
title: ISymUnmanagedWriter::DefineLocalVariable – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: 5730cdd910257d762230f5e54576d5e0a7ac1adb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614822"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable – metoda
Definuje jednu proměnnou v aktuálním lexikálním oboru. Tuto metodu lze volat vícekrát pro proměnnou se stejným názvem, který má více obydlí v celém rozsahu. V tomto případě se však hodnoty `startOffset` `endOffset` parametrů a nesmí překrývat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `name`  
 pro Ukazatel na `WCHAR` , který definuje název místní proměnné.  
  
 `attributes`  
 pro Atributy místních proměnných.  
  
 `cSig`  
 pro `ULONG32`Který udává velikost vyrovnávací paměti v bajtech `signature` .  
  
 `signature`  
 pro Lokální podpis proměnné.  
  
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
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
- [DefineGlobalVariable – metoda](isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2 – metoda](isymunmanagedwriter2-definelocalvariable2-method.md)
