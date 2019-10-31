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
ms.openlocfilehash: 4dc91723f009d46f9c57b1c99aa66ba7a1b127e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126634"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="509ab-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="509ab-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="509ab-103">Získá hodnotu, která označuje, zda je zadaný název shodný s názvem sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="509ab-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="509ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="509ab-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="509ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="509ab-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="509ab-106">pro Název sestavení, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="509ab-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="509ab-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="509ab-107">Return Value</span></span>  
  
|<span data-ttu-id="509ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="509ab-108">HRESULT</span></span>|<span data-ttu-id="509ab-109">Popis</span><span class="sxs-lookup"><span data-stu-id="509ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="509ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="509ab-110">S_OK</span></span>|<span data-ttu-id="509ab-111">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="509ab-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="509ab-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="509ab-112">S_FALSE</span></span>|<span data-ttu-id="509ab-113">Řetězec se v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="509ab-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="509ab-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="509ab-114">E_FAIL</span></span>|<span data-ttu-id="509ab-115">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="509ab-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="509ab-116">Poté, co metoda vrátí E_FAIL, modul Common Language Runtime již nebude v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="509ab-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="509ab-117">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="509ab-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="509ab-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="509ab-118">Requirements</span></span>  
 <span data-ttu-id="509ab-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="509ab-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="509ab-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="509ab-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="509ab-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="509ab-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="509ab-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="509ab-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="509ab-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="509ab-123">See also</span></span>

- [<span data-ttu-id="509ab-124">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="509ab-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="509ab-125">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="509ab-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="509ab-126">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="509ab-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="509ab-127">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="509ab-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
