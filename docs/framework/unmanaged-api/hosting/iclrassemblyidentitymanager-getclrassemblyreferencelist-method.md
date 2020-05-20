---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
ms.openlocfilehash: 7f09cb2264b21fdfbc892069f2c2f0a963b131f8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615966"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="34399-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="34399-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="34399-103">Získá ukazatel rozhraní na instanci [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) ze zadaného seznamu částečných identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="34399-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34399-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34399-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34399-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34399-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="34399-106">pro Pole řetězců ukončených hodnotou null ve formátu "název; vlastnost = hodnota..." které určují seznam identit částečných sestavení.</span><span class="sxs-lookup"><span data-stu-id="34399-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="34399-107">pro Počet položek v `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="34399-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="34399-108">mimo Ukazatel rozhraní na `ICLRAssemblyReferenceList` objekt, který obsahuje data identity sestavení pro seznam sestavení určených v `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="34399-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34399-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="34399-109">Return Value</span></span>  
  
|<span data-ttu-id="34399-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34399-110">HRESULT</span></span>|<span data-ttu-id="34399-111">Popis</span><span class="sxs-lookup"><span data-stu-id="34399-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34399-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="34399-112">S_OK</span></span>|<span data-ttu-id="34399-113">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="34399-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="34399-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34399-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34399-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="34399-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34399-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34399-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34399-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="34399-117">The call timed out.</span></span>|  
|<span data-ttu-id="34399-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34399-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34399-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="34399-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34399-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34399-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34399-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="34399-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34399-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34399-122">E_FAIL</span></span>|<span data-ttu-id="34399-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="34399-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34399-124">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="34399-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34399-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34399-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34399-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34399-126">Requirements</span></span>  
 <span data-ttu-id="34399-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34399-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34399-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34399-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34399-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="34399-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34399-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34399-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34399-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="34399-131">See also</span></span>

- [<span data-ttu-id="34399-132">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34399-132">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="34399-133">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34399-133">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
