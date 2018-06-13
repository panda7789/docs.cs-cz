---
title: ICLRAssemblyReferenceList::IsAssemblyReferenceInList – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b7eeadd532e5a53c693cc1cde59150777d7edc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433864"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="d4642-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="d4642-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="d4642-103">Získá hodnotu, která určuje, zda je zadaný ukazatel odkazuje na sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d4642-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4642-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4642-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4642-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4642-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="d4642-106">[v] Ukazatel rozhraní na sestavení, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d4642-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="d4642-107">Platné hodnoty jsou typu `IAssemblyName` nebo `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d4642-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4642-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4642-108">Return Value</span></span>  
  
|<span data-ttu-id="d4642-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4642-109">HRESULT</span></span>|<span data-ttu-id="d4642-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d4642-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4642-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4642-111">S_OK</span></span>|<span data-ttu-id="d4642-112">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="d4642-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="d4642-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d4642-113">S_FALSE</span></span>|<span data-ttu-id="d4642-114">Řetězec v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="d4642-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="d4642-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4642-115">E_FAIL</span></span>|<span data-ttu-id="d4642-116">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d4642-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4642-117">Po návratu E_FAIL metodu modul common language runtime již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d4642-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="d4642-118">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d4642-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4642-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4642-119">Requirements</span></span>  
 <span data-ttu-id="d4642-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4642-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4642-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4642-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4642-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4642-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4642-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4642-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4642-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4642-124">See Also</span></span>  
 [<span data-ttu-id="d4642-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4642-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d4642-126">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4642-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d4642-127">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4642-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="d4642-128">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4642-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
