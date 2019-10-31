---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: b108c8c87d3afdbfacb569ab501274e5c45c2e2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129179"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
Nastaví posun IL pro obslužnou rutinu catch generovaný kompilátorem, který zabalí asynchronní metodu.  
  
 Posunutí IL vygenerovaného catch je používáno ladicím programem pro zpracování tohoto zachycení, jako by šlo o neuživatelský kód, i když se může vyskytovat v metodě uživatelského kódu. Konkrétně se používá v reakci na událost **CatchHandlerFound** výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
