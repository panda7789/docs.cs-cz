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
ms.openlocfilehash: f1975e5bf20453a3bcd6761d9734be7ddd2ceef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity – metoda
Získá identitu tomto spravovaném objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBSTRGUID`  
 [out] Ukazatel na identifikátor GUID procesu, ve kterém se objekt nachází.  
  
 `AppDomainID`  
 [out] Ukazatel na ID objektu domény aplikace.  
  
 `pCCW`  
 [out] Ukazatel na index objektu v modelu COM classic tabulky v.  
  
## <a name="remarks"></a>Poznámky  
 Identitu spravovaného objektu zahrnuje proces identifikátor GUID, ID domény aplikace a objektu indexu v modelu COM classic tabulky v.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IManagedObject – rozhraní](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
