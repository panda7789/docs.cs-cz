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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ea4947582e4e8bfdb6873a90c5284e9ae9d8a62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736254"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="f4d29-102">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="f4d29-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="f4d29-103">Získá ukazatel na rozhraní umožňující common language runtime (CLR) ke správě identit.</span><span class="sxs-lookup"><span data-stu-id="f4d29-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="f4d29-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f4d29-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d29-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4d29-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4d29-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4d29-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="f4d29-107">[in] A `REFIID` (identifikátor rozhraní), která určuje, které rozhraní pro získání.</span><span class="sxs-lookup"><span data-stu-id="f4d29-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="f4d29-108">Tato hodnota musí být IID_ICLRAssemblyIdentityManager nebo IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="f4d29-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="f4d29-109">[out] Ukazatel na adresu buď [iclrassemblyidentitymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) nebo [iclrhostbindingpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f4d29-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4d29-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4d29-110">Remarks</span></span>  
 <span data-ttu-id="f4d29-111">Volání [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkce získat ukazatel `GetCLRIdentityManager` funkce.</span><span class="sxs-lookup"><span data-stu-id="f4d29-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4d29-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4d29-112">Requirements</span></span>  
 <span data-ttu-id="f4d29-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4d29-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4d29-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4d29-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4d29-115">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="f4d29-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f4d29-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4d29-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d29-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4d29-117">See also</span></span>

- [<span data-ttu-id="f4d29-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f4d29-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
