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
# <a name="getclridentitymanager-function"></a><span data-ttu-id="ee4b7-102">GetCLRIdentityManager – funkce</span><span class="sxs-lookup"><span data-stu-id="ee4b7-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="ee4b7-103">Získá ukazatel na rozhraní, které umožňuje modulu CLR (Common Language Runtime) spravovat identity.</span><span class="sxs-lookup"><span data-stu-id="ee4b7-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="ee4b7-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ee4b7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee4b7-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee4b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee4b7-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="ee4b7-107">pro A `REFIID` (identifikátor rozhraní), který určuje rozhraní, které se má získat.</span><span class="sxs-lookup"><span data-stu-id="ee4b7-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="ee4b7-108">Tato hodnota musí být buď IID_ICLRAssemblyIdentityManager, nebo IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="ee4b7-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="ee4b7-109">mimo Ukazatel na adresu buď [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) , nebo objektu [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ee4b7-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee4b7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee4b7-110">Remarks</span></span>  
 <span data-ttu-id="ee4b7-111">Chcete-li získat ukazatel na funkci, zavolejte funkci [GetRealProcAddress –](getrealprocaddress-function.md) `GetCLRIdentityManager` .</span><span class="sxs-lookup"><span data-stu-id="ee4b7-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4b7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee4b7-112">Requirements</span></span>  
 <span data-ttu-id="ee4b7-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee4b7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee4b7-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ee4b7-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee4b7-115">**Knihovna:** Knihovny Mscorwks. dll</span><span class="sxs-lookup"><span data-stu-id="ee4b7-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="ee4b7-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee4b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee4b7-117">See also</span></span>

- [<span data-ttu-id="ee4b7-118">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ee4b7-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
