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
ms.openlocfilehash: d2b4285cf667bfb929956f23e9dc051e0070fff9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560990"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="91c58-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="91c58-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="91c58-103">Získá [iclrprobingassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerátor pro identity sestavení odkazuje sestavení se zadanou identitou typu.</span><span class="sxs-lookup"><span data-stu-id="91c58-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91c58-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91c58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91c58-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="91c58-106">[in] Platná hodnota, která určuje architekturu procesoru, jak jsou definovány v souboru WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="91c58-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="91c58-107">[in] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="91c58-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="91c58-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je hodnota, která podporuje aktuální verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="91c58-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="91c58-109">[in] Identita vazby neprůhledné sestavení, obvykle vrácená z volání [iclrassemblyidentitymanager::getbindingidentityfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) nebo [iclrassemblyidentitymanager::getbindingidentityfromstream –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="91c58-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="91c58-110">[out] Ukazatel rozhraní k `ICLRProbingAssemblyEnum` enumerátor, který obsahuje odkazy na sestavení odkazuje sestavení identifikované `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="91c58-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91c58-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="91c58-111">Return Value</span></span>  
  
|<span data-ttu-id="91c58-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91c58-112">HRESULT</span></span>|<span data-ttu-id="91c58-113">Popis</span><span class="sxs-lookup"><span data-stu-id="91c58-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91c58-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="91c58-114">S_OK</span></span>|<span data-ttu-id="91c58-115">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="91c58-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="91c58-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91c58-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91c58-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="91c58-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91c58-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91c58-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91c58-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="91c58-119">The call timed out.</span></span>|  
|<span data-ttu-id="91c58-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91c58-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91c58-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="91c58-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91c58-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91c58-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91c58-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="91c58-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91c58-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91c58-124">E_FAIL</span></span>|<span data-ttu-id="91c58-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="91c58-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91c58-126">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="91c58-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91c58-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="91c58-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91c58-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91c58-128">Requirements</span></span>  
 <span data-ttu-id="91c58-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91c58-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c58-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="91c58-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91c58-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91c58-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91c58-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c58-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c58-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91c58-133">See also</span></span>
- [<span data-ttu-id="91c58-134">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91c58-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="91c58-135">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91c58-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="91c58-136">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91c58-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
