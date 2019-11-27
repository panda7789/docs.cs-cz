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
ms.openlocfilehash: 63ba108bc234e566450bb019afc63acb4e75ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427980"
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
 pro `ULONG32`, která indikuje velikost každé `offsets`, `lines`, `columns`, `endLines`a `endColumns` vyrovnávací paměti.  
  
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
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
