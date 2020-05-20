---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441770"
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
 Vrací objekt `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](isymunmanagedasyncmethodpropertieswriter-interface.md)
