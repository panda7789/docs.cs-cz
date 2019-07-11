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
ms.openlocfilehash: 4b2860e811a16406a71d7ab8df123f2b32aaf13e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773294"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="99b7a-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="99b7a-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="99b7a-103">Získá hodnotu určující, zda zadaný název odpovídá názvu sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="99b7a-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99b7a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99b7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99b7a-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="99b7a-106">[in] Název sestavení, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="99b7a-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99b7a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99b7a-107">Return Value</span></span>  
  
|<span data-ttu-id="99b7a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99b7a-108">HRESULT</span></span>|<span data-ttu-id="99b7a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="99b7a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99b7a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="99b7a-110">S_OK</span></span>|<span data-ttu-id="99b7a-111">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="99b7a-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="99b7a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="99b7a-112">S_FALSE</span></span>|<span data-ttu-id="99b7a-113">Řetězec se nezobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="99b7a-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="99b7a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99b7a-114">E_FAIL</span></span>|<span data-ttu-id="99b7a-115">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="99b7a-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99b7a-116">Po vrácení metody E_FAIL, modul common language runtime už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="99b7a-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="99b7a-117">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="99b7a-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99b7a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99b7a-118">Requirements</span></span>  
 <span data-ttu-id="99b7a-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99b7a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b7a-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99b7a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99b7a-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99b7a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99b7a-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b7a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b7a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99b7a-123">See also</span></span>

- [<span data-ttu-id="99b7a-124">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99b7a-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="99b7a-125">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99b7a-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="99b7a-126">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99b7a-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="99b7a-127">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99b7a-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
