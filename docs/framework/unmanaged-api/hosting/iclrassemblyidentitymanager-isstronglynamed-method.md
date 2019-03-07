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
ms.openlocfilehash: a1c1b2d8274baf5fd43991979bc65cd2c2299b46
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484690"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="18e2a-102">ICLRAssemblyIdentityManager::IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="18e2a-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="18e2a-103">Získá hodnotu určující, zda je zadané sestavení silný název.</span><span class="sxs-lookup"><span data-stu-id="18e2a-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18e2a-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18e2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18e2a-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="18e2a-106">[in] Data identity neprůhledné canonical sestavení, sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="18e2a-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="18e2a-107">[out] `true`, pokud sestavení odkazováno `pwzAssemblyIdentity` parametr je silně pojmenované; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="18e2a-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18e2a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18e2a-108">Return Value</span></span>  
  
|<span data-ttu-id="18e2a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18e2a-109">HRESULT</span></span>|<span data-ttu-id="18e2a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="18e2a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18e2a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="18e2a-111">S_OK</span></span>|<span data-ttu-id="18e2a-112">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="18e2a-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="18e2a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18e2a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18e2a-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="18e2a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18e2a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18e2a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18e2a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="18e2a-116">The call timed out.</span></span>|  
|<span data-ttu-id="18e2a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18e2a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18e2a-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="18e2a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18e2a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18e2a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18e2a-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="18e2a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18e2a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18e2a-121">E_FAIL</span></span>|<span data-ttu-id="18e2a-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="18e2a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18e2a-123">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="18e2a-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18e2a-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18e2a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18e2a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18e2a-125">Requirements</span></span>  
 <span data-ttu-id="18e2a-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18e2a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18e2a-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18e2a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18e2a-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18e2a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18e2a-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18e2a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e2a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18e2a-130">See also</span></span>
- [<span data-ttu-id="18e2a-131">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18e2a-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
