---
title: IManagedObject::GetObjectIdentity – metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d014d2900ea790f84331ed933143513ae9e63f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213490"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity – metoda
Získá identitu tohoto spravovaného objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBSTRGUID`  
 [out] Ukazatel na identifikátor GUID procesu, ve kterém se objekt nachází.  
  
 `AppDomainID`  
 [out] Ukazatel na ID objektu domény aplikace.  
  
 `pCCW`  
 [out] Ukazatel na indexu objektu v modelu COM classic tabulce.  
  
## <a name="remarks"></a>Poznámky  
 Identitu spravovaného objektu obsahuje proces identifikátor GUID ID domény aplikace a index objektu v COM classic v-table.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IManagedObject – rozhraní](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
