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
ms.openlocfilehash: ccc787aa1c820a486d9a513055c9c9834b90bd1a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615433"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore – metoda
Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů. Tato metoda se používá ve scénářích pro úpravy a pokračování k aktualizaci úložiště symbolů tak, aby odpovídaly rozdílům v původním přenositelném spustitelném souboru (PE).  
  
> [!NOTE]
> Je nutné zadat pouze jeden z `filename` parametrů nebo `pIStream` , nikoli obojí. `filename`Je-li parametr zadán, bude úložiště symbolů Aktualizováno symboly v tomto souboru. `pIStream`Je-li parametr zadán, bude úložiště Aktualizováno daty z <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateSymbolStore (  
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
