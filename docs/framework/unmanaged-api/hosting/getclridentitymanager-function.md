---
title: GetCLRIdentityManager – funkce
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 8b1e918edf641d38dd6b91d790bcaff8020293a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493263"
---
# <a name="getclridentitymanager-function"></a>GetCLRIdentityManager – funkce
Získá ukazatel na rozhraní, které umožňuje modulu CLR (Common Language Runtime) spravovat identity.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 pro A `REFIID` (identifikátor rozhraní), který určuje rozhraní, které se má získat. Tato hodnota musí být buď IID_ICLRAssemblyIdentityManager, nebo IID_ICLRHostBindingPolicyManager.  
  
 `ppManager`  
 mimo Ukazatel na adresu buď [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) , nebo objektu [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat ukazatel na funkci, zavolejte funkci [GetRealProcAddress –](getrealprocaddress-function.md) `GetCLRIdentityManager` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Knihovny Mscorwks. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
