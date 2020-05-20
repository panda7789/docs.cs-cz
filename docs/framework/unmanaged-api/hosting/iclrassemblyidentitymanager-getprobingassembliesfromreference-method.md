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
ms.openlocfilehash: 98af9931e219c384b017d3c70fe21cdb6e052ac1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615953"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="01b96-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="01b96-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="01b96-103">Získá enumerátor [ICLRProbingAssemblyEnum –](iclrprobingassemblyenum-interface.md) pro identity sestavení odkazované sestavením se zadaným typem identity.</span><span class="sxs-lookup"><span data-stu-id="01b96-103">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01b96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01b96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01b96-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="01b96-106">pro Platná hodnota, která určuje architekturu procesoru, jak je definováno v souboru WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="01b96-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="01b96-107">pro K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="01b96-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="01b96-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou aktuální verze modulu CLR (Common Language Runtime) podporuje.</span><span class="sxs-lookup"><span data-stu-id="01b96-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="01b96-109">pro Neprůhledná identita vazby sestavení, která se obvykle vrací voláním metody [ICLRAssemblyIdentityManager:: getbindingidentityfromfile –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) nebo [ICLRAssemblyIdentityManager:: getbindingidentityfromstream –](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) .</span><span class="sxs-lookup"><span data-stu-id="01b96-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="01b96-110">mimo Ukazatel rozhraní na `ICLRProbingAssemblyEnum` enumerátor, který obsahuje odkazy na sestavení, na která odkazuje sestavení identifikované `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="01b96-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01b96-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01b96-111">Return Value</span></span>  
  
|<span data-ttu-id="01b96-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01b96-112">HRESULT</span></span>|<span data-ttu-id="01b96-113">Popis</span><span class="sxs-lookup"><span data-stu-id="01b96-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01b96-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="01b96-114">S_OK</span></span>|<span data-ttu-id="01b96-115">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="01b96-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="01b96-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01b96-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01b96-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="01b96-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01b96-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01b96-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01b96-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="01b96-119">The call timed out.</span></span>|  
|<span data-ttu-id="01b96-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01b96-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01b96-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="01b96-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01b96-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01b96-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01b96-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="01b96-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01b96-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01b96-124">E_FAIL</span></span>|<span data-ttu-id="01b96-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="01b96-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01b96-126">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="01b96-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01b96-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01b96-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01b96-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01b96-128">Requirements</span></span>  
 <span data-ttu-id="01b96-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b96-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b96-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01b96-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01b96-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01b96-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01b96-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b96-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b96-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="01b96-133">See also</span></span>

- [<span data-ttu-id="01b96-134">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01b96-134">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="01b96-135">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01b96-135">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="01b96-136">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01b96-136">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
