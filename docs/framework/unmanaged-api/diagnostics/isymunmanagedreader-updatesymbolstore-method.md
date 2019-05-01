---
title: ISymUnmanagedReader::UpdateSymbolStore – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f62c954bf9d73ab564eba388e742794a330362d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986320"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore – metoda
Aktualizuje existující úložiště symbolů do úložiště symbolů delta. Tato metoda se používá ve scénářích edit-and-continue aktualizovat úložiště symbolů tak, aby odpovídaly rozdíly do původní přenosného spustitelného souboru (PE).  
  
> [!NOTE]
>  Je nutné zadat pouze jeden z `filename` nebo `pIStream` parametrů, ne obojí. Pokud `filename` není zadán, aktualizuje úložiště symbolů se symboly v daném souboru. Pokud `pIStream` není zadána, úložiště se aktualizuje s daty z <xref:System.Runtime.InteropServices.ComTypes.IStream>.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 [in] Název souboru, který obsahuje úložiště symbolů.  
  
 `pIStream`  
 [in] Datový proud souboru použít jako alternativu k `filename` parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
