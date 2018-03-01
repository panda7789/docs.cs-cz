---
title: "ISymUnmanagedWriter::DefineSequencePoints – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e1dcc427a6d034ce108ca66f71cc24b1050a72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>ISymUnmanagedWriter::DefineSequencePoints – metoda
Definuje skupinu bodů pořadí v rámci aktuální metoda. Každý počáteční řádek a počáteční sloupec definovat spuštění příkazu v rámci metody. Každý ukončení řádku a končí sloupec definovat konci příkazu v rámci metody. Pole musí být seřazeny ve vzestupném pořadí odsazení. Posun je vždy měří od začátku metodu v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `document`  
 [v] Dokument objekt, pro které jsou definovány body sekvence.  
  
 `spCount`  
 [v] A `ULONG32` , která určuje velikost jednotlivých `offsets`, `lines`, `columns`, `endLines`, a `endColumns` vyrovnávací paměti.  
  
 `offsets`  
 [v] Posun body sekvence se měří od začátku metody.  
  
 `lines`  
 [v] Počáteční řádek čísla bodů pořadí.  
  
 `columns`  
 [v] Počáteční sloupec čísla body sekvence.  
  
 `endLines`  
 [v] Koncová čísla řádků bodů pořadí. Tento parametr je volitelný.  
  
 `endColumns`  
 [v] Koncová čísla sloupců body sekvence. Tento parametr je volitelný.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
