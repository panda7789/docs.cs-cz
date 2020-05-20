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
ms.openlocfilehash: 91f174cab4986882df795eb531baedfc0dd43962
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615862"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="4edc0-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="4edc0-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="4edc0-103">Získá hodnotu, která označuje, zda je zadaný název shodný s názvem sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4edc0-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4edc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4edc0-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4edc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4edc0-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="4edc0-106">pro Název sestavení, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="4edc0-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4edc0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4edc0-107">Return Value</span></span>  
  
|<span data-ttu-id="4edc0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4edc0-108">HRESULT</span></span>|<span data-ttu-id="4edc0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4edc0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4edc0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4edc0-110">S_OK</span></span>|<span data-ttu-id="4edc0-111">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4edc0-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="4edc0-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4edc0-112">S_FALSE</span></span>|<span data-ttu-id="4edc0-113">Řetězec se v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="4edc0-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="4edc0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4edc0-114">E_FAIL</span></span>|<span data-ttu-id="4edc0-115">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4edc0-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4edc0-116">Jakmile metoda vrátí E_FAIL, modul CLR (Common Language Runtime) již nebude v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4edc0-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="4edc0-117">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4edc0-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4edc0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4edc0-118">Requirements</span></span>  
 <span data-ttu-id="4edc0-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4edc0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4edc0-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4edc0-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4edc0-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4edc0-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4edc0-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4edc0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4edc0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4edc0-123">See also</span></span>

- [<span data-ttu-id="4edc0-124">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4edc0-124">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="4edc0-125">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4edc0-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4edc0-126">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4edc0-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="4edc0-127">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4edc0-127">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
