---
title: ICLRAssemblyIdentityManager::IsStronglyNamed – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 735ff725bc06c14da9821055a6a143f857548c30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434464"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="951fb-102">ICLRAssemblyIdentityManager::IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="951fb-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="951fb-103">Získá hodnotu, která určuje, zda zadané sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="951fb-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="951fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="951fb-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="951fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="951fb-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="951fb-106">[v] Identifikační údaje neprůhledného kanonický sestavení sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="951fb-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="951fb-107">[out] `true`, pokud je sestavení odkazuje `pwzAssemblyIdentity` parametr je silně pojmenované, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="951fb-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="951fb-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="951fb-108">Return Value</span></span>  
  
|<span data-ttu-id="951fb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="951fb-109">HRESULT</span></span>|<span data-ttu-id="951fb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="951fb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="951fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="951fb-111">S_OK</span></span>|<span data-ttu-id="951fb-112">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="951fb-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="951fb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="951fb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="951fb-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="951fb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="951fb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="951fb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="951fb-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="951fb-116">The call timed out.</span></span>|  
|<span data-ttu-id="951fb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="951fb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="951fb-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="951fb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="951fb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="951fb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="951fb-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="951fb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="951fb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="951fb-121">E_FAIL</span></span>|<span data-ttu-id="951fb-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="951fb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="951fb-123">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="951fb-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="951fb-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="951fb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="951fb-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="951fb-125">Requirements</span></span>  
 <span data-ttu-id="951fb-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="951fb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="951fb-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="951fb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="951fb-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="951fb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="951fb-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="951fb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="951fb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="951fb-130">See Also</span></span>  
 [<span data-ttu-id="951fb-131">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="951fb-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
