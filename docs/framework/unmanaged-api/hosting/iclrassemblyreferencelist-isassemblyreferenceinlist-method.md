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
ms.openlocfilehash: 4e75b8553ff33946654a6a3b6184f98049c6a6cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126670"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="a13c7-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="a13c7-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="a13c7-103">Získá hodnotu, která označuje, zda zadaný ukazatel odkazuje na sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="a13c7-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a13c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a13c7-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a13c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a13c7-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="a13c7-106">pro Ukazatel rozhraní na sestavení, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="a13c7-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="a13c7-107">Platné hodnoty jsou typu `IAssemblyName` nebo `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="a13c7-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a13c7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a13c7-108">Return Value</span></span>  
  
|<span data-ttu-id="a13c7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a13c7-109">HRESULT</span></span>|<span data-ttu-id="a13c7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a13c7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a13c7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a13c7-111">S_OK</span></span>|<span data-ttu-id="a13c7-112">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="a13c7-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="a13c7-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a13c7-113">S_FALSE</span></span>|<span data-ttu-id="a13c7-114">Řetězec se v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="a13c7-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="a13c7-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a13c7-115">E_FAIL</span></span>|<span data-ttu-id="a13c7-116">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a13c7-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a13c7-117">Poté, co metoda vrátí E_FAIL, modul Common Language Runtime již nebude v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a13c7-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="a13c7-118">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a13c7-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a13c7-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a13c7-119">Requirements</span></span>  
 <span data-ttu-id="a13c7-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a13c7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a13c7-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a13c7-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a13c7-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a13c7-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a13c7-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a13c7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13c7-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a13c7-124">See also</span></span>

- [<span data-ttu-id="a13c7-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a13c7-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a13c7-126">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a13c7-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a13c7-127">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a13c7-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="a13c7-128">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a13c7-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
