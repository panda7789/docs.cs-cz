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
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939010"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>ISymUnmanagedReader::UpdateSymbolStore – metoda
Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů. Tato metoda se používá ve scénářích pro úpravy a pokračování k aktualizaci úložiště symbolů tak, aby odpovídaly rozdílům v původním přenositelném spustitelném souboru (PE).  
  
> [!NOTE]
> Je nutné zadat pouze jeden z `filename` parametrů nebo `pIStream` , nikoli obojí. Je `filename` -li parametr zadán, bude úložiště symbolů Aktualizováno symboly v tomto souboru. Je `pIStream` -li parametr zadán, bude úložiště Aktualizováno daty <xref:System.Runtime.InteropServices.ComTypes.IStream>z.  
  
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
 pro Datový proud souboru, který se používá jako alternativa `filename` k parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; jinak E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlaviček** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
