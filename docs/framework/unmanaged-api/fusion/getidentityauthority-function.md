---
title: GetIdentityAuthority – funkce
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f29246bdb929c8eaf1ebce726164d5cd2269b9f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796869"
---
# <a name="getidentityauthority-function"></a>GetIdentityAuthority – funkce
Získá ukazatel na instanci [IIdentityAuthority –](iidentityauthority-interface.md) , která spravuje klíče pro objekty kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppIIdentityAuthority`  
 mimo Vrácený `IIdentityAuthority` ukazatel.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IIdentityAuthority – rozhraní](iidentityauthority-interface.md)
- [Globální statické funkce pro fúze](fusion-global-static-functions.md)
