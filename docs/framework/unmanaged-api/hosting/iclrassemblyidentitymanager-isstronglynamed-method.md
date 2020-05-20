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
ms.openlocfilehash: d388f366671f50c3dcb3bd9d387300dd1bbb168f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615901"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="dc5a5-102">ICLRAssemblyIdentityManager::IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="dc5a5-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="dc5a5-103">Získá hodnotu, která označuje, zda je zadané sestavení silně pojmenované.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc5a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc5a5-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc5a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc5a5-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="dc5a5-106">pro Neprůhledná data identity kanonického sestavení pro sestavení, která mají být vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="dc5a5-107">[out] `true` Pokud je sestavení odkazované `pwzAssemblyIdentity` parametrem silně pojmenované, v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="dc5a5-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc5a5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc5a5-108">Return Value</span></span>  
  
|<span data-ttu-id="dc5a5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc5a5-109">HRESULT</span></span>|<span data-ttu-id="dc5a5-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dc5a5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc5a5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc5a5-111">S_OK</span></span>|<span data-ttu-id="dc5a5-112">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="dc5a5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc5a5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc5a5-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc5a5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc5a5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc5a5-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-116">The call timed out.</span></span>|  
|<span data-ttu-id="dc5a5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc5a5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc5a5-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc5a5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc5a5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc5a5-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc5a5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc5a5-121">E_FAIL</span></span>|<span data-ttu-id="dc5a5-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc5a5-123">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc5a5-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dc5a5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc5a5-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc5a5-125">Requirements</span></span>  
 <span data-ttu-id="dc5a5-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc5a5-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc5a5-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dc5a5-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc5a5-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc5a5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc5a5-129">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc5a5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc5a5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc5a5-130">See also</span></span>

- [<span data-ttu-id="dc5a5-131">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc5a5-131">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
