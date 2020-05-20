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
ms.openlocfilehash: 57f771d933e896677dfc0bd5d9dac58da2af22c8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617253"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="0116f-102">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="0116f-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="0116f-103">Získá ukazatel na rozhraní, které umožňuje modulu CLR (Common Language Runtime) spravovat identity.</span><span class="sxs-lookup"><span data-stu-id="0116f-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="0116f-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0116f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0116f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0116f-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0116f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0116f-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="0116f-107">pro A `REFIID` (identifikátor rozhraní), který určuje rozhraní, které se má získat.</span><span class="sxs-lookup"><span data-stu-id="0116f-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="0116f-108">Tato hodnota musí být buď IID_ICLRAssemblyIdentityManager, nebo IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="0116f-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="0116f-109">mimo Ukazatel na adresu buď [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) , nebo objektu [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0116f-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0116f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0116f-110">Remarks</span></span>  
 <span data-ttu-id="0116f-111">Chcete-li získat ukazatel na funkci, zavolejte funkci [GetRealProcAddress –](getrealprocaddress-function.md) `GetCLRIdentityManager` .</span><span class="sxs-lookup"><span data-stu-id="0116f-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0116f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0116f-112">Requirements</span></span>  
 <span data-ttu-id="0116f-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0116f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0116f-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0116f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0116f-115">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="0116f-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0116f-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0116f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0116f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0116f-117">See also</span></span>

- [<span data-ttu-id="0116f-118">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="0116f-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
