---
title: ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: ed3c841c34b71b30f740117899353aa289e478d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614705"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a>ISymUnmanagedWriter2::DefineGlobalVariable2 – metoda
Definuje jednu globální proměnnou.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 pro Název globální proměnné  
  
 `attributes`  
 pro Atributy globálních proměnných.  
  
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
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter2 – rozhraní](isymunmanagedwriter2-interface.md)
- [DefineGlobalVariable – metoda](isymunmanagedwriter-defineglobalvariable-method.md)
