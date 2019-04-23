---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de17a91b5093372579a4d9435532a95406addd0a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216896"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="bda55-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="bda55-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="bda55-103">Získá hodnotu určující, zda zadaný název odpovídá názvu sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="bda55-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bda55-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bda55-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="bda55-106">[in] Název sestavení, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="bda55-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bda55-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bda55-107">Return Value</span></span>  
  
|<span data-ttu-id="bda55-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bda55-108">HRESULT</span></span>|<span data-ttu-id="bda55-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bda55-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bda55-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bda55-110">S_OK</span></span>|<span data-ttu-id="bda55-111">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="bda55-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="bda55-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bda55-112">S_FALSE</span></span>|<span data-ttu-id="bda55-113">Řetězec se nezobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="bda55-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="bda55-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bda55-114">E_FAIL</span></span>|<span data-ttu-id="bda55-115">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="bda55-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bda55-116">Po vrácení metody E_FAIL, modul common language runtime už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="bda55-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="bda55-117">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bda55-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bda55-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bda55-118">Requirements</span></span>  
 <span data-ttu-id="bda55-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bda55-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda55-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bda55-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bda55-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bda55-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bda55-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda55-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda55-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bda55-123">See also</span></span>

- [<span data-ttu-id="bda55-124">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bda55-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="bda55-125">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bda55-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bda55-126">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bda55-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="bda55-127">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bda55-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
