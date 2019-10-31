---
title: GetAppIdAuthority – funkce
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: 22a6af61251942f068676daaee2bdfa868e32a97
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134558"
---
# <a name="getappidauthority-function"></a>GetAppIdAuthority – funkce
Získá ukazatel na instanci [IAppIdAuthority –](iappidauthority-interface.md) , která spravuje klíče pro identity aplikace a odkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppIAppIdAuthority`  
 mimo Vrácený ukazatel `IAppIdAuthority`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAppIdAuthority – rozhraní](iappidauthority-interface.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
