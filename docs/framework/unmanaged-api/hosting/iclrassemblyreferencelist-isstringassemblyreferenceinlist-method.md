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
ms.openlocfilehash: ad7230731775cbc56dd0f1eaed72df19512d3733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432593"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="6f984-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="6f984-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="6f984-103">Získá hodnotu, která určuje, zda zadaný název odpovídá názvu sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6f984-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f984-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f984-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f984-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f984-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="6f984-106">[v] Název sestavení, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="6f984-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f984-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f984-107">Return Value</span></span>  
  
|<span data-ttu-id="6f984-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f984-108">HRESULT</span></span>|<span data-ttu-id="6f984-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6f984-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f984-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f984-110">S_OK</span></span>|<span data-ttu-id="6f984-111">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6f984-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="6f984-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6f984-112">S_FALSE</span></span>|<span data-ttu-id="6f984-113">Řetězec v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="6f984-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="6f984-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f984-114">E_FAIL</span></span>|<span data-ttu-id="6f984-115">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="6f984-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f984-116">Po návratu E_FAIL metodu modul common language runtime již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6f984-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="6f984-117">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f984-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f984-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f984-118">Requirements</span></span>  
 <span data-ttu-id="6f984-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f984-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f984-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f984-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f984-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f984-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f984-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f984-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f984-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f984-123">See Also</span></span>  
 [<span data-ttu-id="6f984-124">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f984-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="6f984-125">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f984-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="6f984-126">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f984-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="6f984-127">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f984-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
