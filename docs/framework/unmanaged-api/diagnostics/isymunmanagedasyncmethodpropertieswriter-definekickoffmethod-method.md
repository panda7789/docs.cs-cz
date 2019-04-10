---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226609"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
Nastaví výchozí metodu, která zahájí asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
