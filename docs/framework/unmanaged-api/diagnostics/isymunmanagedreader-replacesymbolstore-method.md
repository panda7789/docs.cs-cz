---
title: ISymUnmanagedReader::ReplaceSymbolStore – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 525ec4828fb942aeb447940ea68a523cd7c69140
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736737"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore – metoda
Nahradí existující úložiště symbolů do úložiště symbolů delta. Tato metoda je podobný [updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) metody, s tím rozdílem, že daný delta funguje jako o úplné nahrazení spíše než aktualizace.  
  
> [!NOTE]
>  Je nutné zadat pouze jeden z `filename` nebo `pIStream` parametrů, ne obojí. Pokud `filename` není zadán, aktualizuje úložiště symbolů se symboly v daném souboru. Pokud `pIStream` není zadána, úložiště se aktualizuje s daty z <xref:System.Runtime.InteropServices.ComTypes.IStream>.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReplaceSymbolStore (  
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
