---
title: "ICLRAssemblyIdentityManager::IsStronglyNamed – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.IsStronglyNamed
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0cb0bcaf5d19ec088511e64baffff9031911b32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="ae871-102">ICLRAssemblyIdentityManager::IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="ae871-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="ae871-103">Získá hodnotu, která určuje, zda zadané sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="ae871-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae871-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae871-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae871-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae871-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="ae871-106">[v] Identifikační údaje neprůhledného kanonický sestavení sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="ae871-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="ae871-107">[out] `true`, pokud je sestavení odkazuje `pwzAssemblyIdentity` parametr je silně pojmenované, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="ae871-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae871-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ae871-108">Return Value</span></span>  
  
|<span data-ttu-id="ae871-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae871-109">HRESULT</span></span>|<span data-ttu-id="ae871-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ae871-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae871-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae871-111">S_OK</span></span>|<span data-ttu-id="ae871-112">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ae871-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="ae871-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae871-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae871-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ae871-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ae871-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ae871-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ae871-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ae871-116">The call timed out.</span></span>|  
|<span data-ttu-id="ae871-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ae871-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ae871-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ae871-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ae871-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ae871-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ae871-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ae871-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ae871-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae871-121">E_FAIL</span></span>|<span data-ttu-id="ae871-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ae871-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ae871-123">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ae871-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ae871-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ae871-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae871-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae871-125">Requirements</span></span>  
 <span data-ttu-id="ae871-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae871-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae871-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae871-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae871-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae871-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae871-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae871-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae871-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae871-130">See Also</span></span>  
 [<span data-ttu-id="ae871-131">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae871-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
