---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26423837c173b5f18282a8aa480ae92ecc452489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435651"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="ed14f-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="ed14f-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="ed14f-103">Získá [iclrprobingassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerátor pro identity sestavení odkazuje sestavení s typem zadanou identitou.</span><span class="sxs-lookup"><span data-stu-id="ed14f-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed14f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed14f-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed14f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed14f-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="ed14f-106">[v] Platná hodnota, která určuje architekturu procesoru, jak jsou definovány v souboru WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="ed14f-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ed14f-107">[v] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ed14f-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ed14f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ed14f-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="ed14f-109">[v] Vazba identity neprůhledného sestavení, obvykle vrácená z volání [iclrassemblyidentitymanager::getbindingidentityfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) nebo [iclrassemblyidentitymanager::getbindingidentityfromstream –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ed14f-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="ed14f-110">[out] Ukazatele rozhraní k `ICLRProbingAssemblyEnum` enumerátor, který obsahuje odkazy na sestavení odkazuje sestavení identifikovaný `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="ed14f-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed14f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed14f-111">Return Value</span></span>  
  
|<span data-ttu-id="ed14f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed14f-112">HRESULT</span></span>|<span data-ttu-id="ed14f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ed14f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed14f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed14f-114">S_OK</span></span>|<span data-ttu-id="ed14f-115">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ed14f-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="ed14f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed14f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed14f-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ed14f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ed14f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ed14f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ed14f-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ed14f-119">The call timed out.</span></span>|  
|<span data-ttu-id="ed14f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ed14f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ed14f-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ed14f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ed14f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ed14f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ed14f-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ed14f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ed14f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ed14f-124">E_FAIL</span></span>|<span data-ttu-id="ed14f-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ed14f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ed14f-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ed14f-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ed14f-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ed14f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed14f-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed14f-128">Requirements</span></span>  
 <span data-ttu-id="ed14f-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed14f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed14f-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed14f-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed14f-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed14f-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed14f-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed14f-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed14f-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed14f-133">See Also</span></span>  
 [<span data-ttu-id="ed14f-134">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed14f-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ed14f-135">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed14f-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="ed14f-136">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed14f-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
