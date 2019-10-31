---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
ms.openlocfilehash: 65dc330e88cb2457cc34f9994313373ab1ab84aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126705"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="ecc83-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="ecc83-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="ecc83-103">Získá instanci [ICLRReferenceAssemblyEnum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) , která obsahuje seznam sestavení, na která odkazuje sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="ecc83-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecc83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecc83-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="ecc83-106">pro Cesta k sestavení, které má být vyhodnoceno.</span><span class="sxs-lookup"><span data-stu-id="ecc83-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ecc83-107">pro K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ecc83-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ecc83-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou aktuální verze modulu CLR (Common Language Runtime) podporuje.</span><span class="sxs-lookup"><span data-stu-id="ecc83-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="ecc83-109">pro Ukazatel na objekt [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který představuje sestavení, která by měla být vyloučena z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="ecc83-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="ecc83-110">mimo Ukazatel na adresu `ICLRReferenceAssemblyEnum` objektu, který obsahuje data identity sestavení pro sestavení, na která je odkazováno sestavením v `pwzFilePath`, s výjimkou sestavení reprezentovaných `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="ecc83-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecc83-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ecc83-111">Return Value</span></span>  
  
|<span data-ttu-id="ecc83-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecc83-112">HRESULT</span></span>|<span data-ttu-id="ecc83-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc83-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecc83-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecc83-114">S_OK</span></span>|<span data-ttu-id="ecc83-115">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ecc83-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="ecc83-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecc83-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecc83-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ecc83-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecc83-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecc83-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecc83-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ecc83-119">The call timed out.</span></span>|  
|<span data-ttu-id="ecc83-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecc83-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecc83-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ecc83-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecc83-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecc83-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecc83-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="ecc83-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecc83-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecc83-124">E_FAIL</span></span>|<span data-ttu-id="ecc83-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="ecc83-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecc83-126">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="ecc83-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecc83-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ecc83-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecc83-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecc83-128">Remarks</span></span>  
 <span data-ttu-id="ecc83-129">Volající může zvolit vyloučení sady známých odkazů na sestavení ze vráceného seznamu.</span><span class="sxs-lookup"><span data-stu-id="ecc83-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="ecc83-130">Tato sada je definována parametrem `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="ecc83-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc83-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecc83-131">Requirements</span></span>  
 <span data-ttu-id="ecc83-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc83-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc83-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ecc83-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecc83-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecc83-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc83-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc83-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc83-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecc83-136">See also</span></span>

- [<span data-ttu-id="ecc83-137">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecc83-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ecc83-138">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecc83-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ecc83-139">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecc83-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
