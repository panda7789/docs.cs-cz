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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615446"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>ISymUnmanagedReader::ReplaceSymbolStore – metoda
Nahradí existující úložiště symbolů rozdílovým úložištěm symbolů. Tato metoda je podobná metodě [UpdateSymbolStore –](isymunmanagedreader-updatesymbolstore-method.md) , s tím rozdílem, že daný rozdíl funguje jako kompletní náhrada, nikoli jako aktualizace.  
  
> [!NOTE]
> Je nutné zadat pouze jeden z `filename` parametrů nebo `pIStream` , nikoli obojí. `filename`Je-li parametr zadán, bude úložiště symbolů Aktualizováno symboly v tomto souboru. `pIStream`Je-li parametr zadán, bude úložiště Aktualizováno daty z <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 pro Název souboru, který obsahuje úložiště symbolů.  
  
 `pIStream`  
 pro Datový proud souboru, který se používá jako alternativa k `filename` parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedReader – rozhraní](isymunmanagedreader-interface.md)
