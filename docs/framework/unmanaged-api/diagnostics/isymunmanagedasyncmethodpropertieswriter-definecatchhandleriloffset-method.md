---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset – metoda
Nastaví IL posunutí pro generované kompilátorem catch obslužná rutina, která zabalí asynchronní metody.  
  
 Posun IL generovaného catch je používán ladicího programu pro zpracování catch, jako by šlo bez uživatelského kódu, i když můžou nastat ve metodu kódu uživatele. Konkrétně se používá v reakci **CatchHandlerFound** události výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
