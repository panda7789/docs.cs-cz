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
ms.openlocfilehash: e6a95a636623f0b4ea75706039194572ecf1bbe0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136198"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="57422-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="57422-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="57422-103">Získá hodnotu určující, zda zadaný ukazatel odkazuje na sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="57422-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57422-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57422-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57422-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57422-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="57422-106">[in] Ukazatel rozhraní k sestavení, pro který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="57422-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="57422-107">Platné hodnoty jsou typu `IAssemblyName` nebo `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="57422-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57422-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="57422-108">Return Value</span></span>  
  
|<span data-ttu-id="57422-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57422-109">HRESULT</span></span>|<span data-ttu-id="57422-110">Popis</span><span class="sxs-lookup"><span data-stu-id="57422-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57422-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57422-111">S_OK</span></span>|<span data-ttu-id="57422-112">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="57422-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="57422-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="57422-113">S_FALSE</span></span>|<span data-ttu-id="57422-114">Řetězec se nezobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="57422-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="57422-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57422-115">E_FAIL</span></span>|<span data-ttu-id="57422-116">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="57422-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57422-117">Po vrácení metody E_FAIL, modul common language runtime už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="57422-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="57422-118">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57422-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57422-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57422-119">Requirements</span></span>  
 <span data-ttu-id="57422-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57422-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57422-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57422-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57422-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57422-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57422-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57422-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57422-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57422-124">See also</span></span>

- [<span data-ttu-id="57422-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57422-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="57422-126">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57422-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="57422-127">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57422-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="57422-128">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57422-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
