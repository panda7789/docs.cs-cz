---
title: ISymUnmanagedWriter::Initialize2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 869d7d36ac24bfeee5b2361dd569945ad77eaf7f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610064"
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 – metoda
Nastaví rozhraní Emit metadat, ke kterému bude tento zapisovač přidružen, a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění. Tato metoda také umožňuje nastavit konečné umístění souboru databáze programu (PDB).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a>Parametry  
 `emitter`  
 pro Ukazatel na rozhraní Emit metadat.  
  
 `tempfilename`  
 pro Ukazatel na `WCHAR` , který obsahuje název souboru, do kterého jsou zapsány symboly ladění. Pokud je název souboru zadán pro zapisovač, který nepoužívá názvy souborů, tento parametr je ignorován.  
  
 `pIStream`  
 pro Je-li tento parametr zadán, zapisovač symbolů vygeneruje symboly do zadaného <xref:System.Runtime.InteropServices.ComTypes.IStream> souboru, nikoli do souboru zadaného v `filename` parametru. `pIStream`Parametr je nepovinný.  
  
 `fFullBuild`  
 [in] `true` Pokud se jedná o úplné opětovné sestavení; `false`Pokud se jedná o přírůstkovou kompilaci.  
  
 `finalfilename`  
 pro Ukazatel na `WCHAR` řetězec, který je cestou k konečnému umístění souboru PDB.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
- [Initialize – metoda](isymunmanagedwriter-initialize-method.md)
