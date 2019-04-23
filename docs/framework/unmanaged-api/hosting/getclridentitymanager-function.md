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
ms.openlocfilehash: 84f71266d84cc98c2a5deb4aa8639e36808315a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130179"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="0a3d5-102">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="0a3d5-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="0a3d5-103">Získá ukazatel na rozhraní umožňující common language runtime (CLR) ke správě identit.</span><span class="sxs-lookup"><span data-stu-id="0a3d5-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="0a3d5-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a3d5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3d5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a3d5-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a3d5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a3d5-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="0a3d5-107">[in] A `REFIID` (identifikátor rozhraní), která určuje, které rozhraní pro získání.</span><span class="sxs-lookup"><span data-stu-id="0a3d5-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="0a3d5-108">Tato hodnota musí být IID_ICLRAssemblyIdentityManager nebo IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="0a3d5-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="0a3d5-109">[out] Ukazatel na adresu buď [iclrassemblyidentitymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) nebo [iclrhostbindingpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="0a3d5-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a3d5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a3d5-110">Remarks</span></span>  
 <span data-ttu-id="0a3d5-111">Volání [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkce získat ukazatel `GetCLRIdentityManager` funkce.</span><span class="sxs-lookup"><span data-stu-id="0a3d5-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a3d5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a3d5-112">Requirements</span></span>  
 <span data-ttu-id="0a3d5-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a3d5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a3d5-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a3d5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a3d5-115">**Knihovna:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="0a3d5-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0a3d5-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a3d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3d5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a3d5-117">See also</span></span>

- [<span data-ttu-id="0a3d5-118">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="0a3d5-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
