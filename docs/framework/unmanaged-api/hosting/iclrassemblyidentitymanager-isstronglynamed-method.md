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
ms.openlocfilehash: f9d201c3753a8e71ea3da0b0f4f8a3a47e5bcee2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773370"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="d5be7-102">ICLRAssemblyIdentityManager::IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="d5be7-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="d5be7-103">Získá hodnotu určující, zda je zadané sestavení silný název.</span><span class="sxs-lookup"><span data-stu-id="d5be7-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5be7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5be7-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5be7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5be7-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="d5be7-106">[in] Data identity neprůhledné canonical sestavení, sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="d5be7-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="d5be7-107">[out] `true`, pokud sestavení odkazováno `pwzAssemblyIdentity` parametr je silně pojmenované; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d5be7-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5be7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5be7-108">Return Value</span></span>  
  
|<span data-ttu-id="d5be7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5be7-109">HRESULT</span></span>|<span data-ttu-id="d5be7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d5be7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5be7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5be7-111">S_OK</span></span>|<span data-ttu-id="d5be7-112">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="d5be7-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="d5be7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5be7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5be7-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d5be7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5be7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5be7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5be7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d5be7-116">The call timed out.</span></span>|  
|<span data-ttu-id="d5be7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5be7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5be7-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d5be7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5be7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5be7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5be7-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d5be7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5be7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5be7-121">E_FAIL</span></span>|<span data-ttu-id="d5be7-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d5be7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5be7-123">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d5be7-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5be7-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5be7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5be7-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5be7-125">Requirements</span></span>  
 <span data-ttu-id="d5be7-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5be7-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5be7-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5be7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5be7-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5be7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5be7-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5be7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5be7-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5be7-130">See also</span></span>

- [<span data-ttu-id="d5be7-131">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5be7-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
