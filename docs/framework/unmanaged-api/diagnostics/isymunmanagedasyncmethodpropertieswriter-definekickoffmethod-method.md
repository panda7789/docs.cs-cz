---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: ccf1287a1b0218e7f2560e1afbb0930c93b43263
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129175"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod – metoda
Nastaví počáteční metodu, která inicializuje asynchronní operaci.  
  
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
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
