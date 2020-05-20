---
title: ISymUnmanagedWriter::DefineSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614796"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints – metoda
Definuje skupinu bodů sekvence v rámci aktuální metody. Každý počáteční řádek a počáteční sloupec definují začátek příkazu v rámci metody. Každý koncový řádek a koncový sloupec definují konec příkazu v rámci metody. Pole by se měla seřadit ve vzestupném pořadí posunů. Posun je vždy měřen od začátku metody (v bajtech).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 pro Objekt dokumentu, pro který jsou definovány body sekvence.  
  
 `spCount`  
 pro `ULONG32`Který označuje velikost jednotlivých `offsets` `lines` `columns` `endLines` `endColumns` vyrovnávacích pamětí,,, a.  
  
 `offsets`  
 pro Posun bodů sekvence měřený od začátku metody  
  
 `lines`  
 pro Počáteční čísla řádků bodů sekvence.  
  
 `columns`  
 pro Čísla počátečních sloupců bodů sekvence  
  
 `endLines`  
 pro Koncová čísla řádků bodů sekvence. Tento parametr je volitelný.  
  
 `endColumns`  
 pro Čísla koncových sloupců bodů sekvence. Tento parametr je volitelný.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
