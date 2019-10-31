---
title: ModuleBindInfo – struktura
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133751"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="e3647-102">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="e3647-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="e3647-103">Obsahuje podrobné informace o odkazovaném modulu a sestavení, které ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e3647-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3647-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3647-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e3647-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e3647-105">Members</span></span>  
  
|<span data-ttu-id="e3647-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e3647-106">Member</span></span>|<span data-ttu-id="e3647-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e3647-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="e3647-108">Jedinečný identifikátor pro `IStream`, který je vrácen voláním metody [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) , ze které má být načten odkazovaný modul.</span><span class="sxs-lookup"><span data-stu-id="e3647-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="e3647-109">Jedinečný identifikátor pro sestavení, které obsahuje odkazovaný modul.</span><span class="sxs-lookup"><span data-stu-id="e3647-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="e3647-110">Název odkazovaného modulu</span><span class="sxs-lookup"><span data-stu-id="e3647-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3647-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3647-111">Remarks</span></span>  
 <span data-ttu-id="e3647-112">`ModuleBindInfo` se předává jako parametr pro `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="e3647-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="e3647-113">Hostitel dodá jedinečný identifikátor `dwAppDomainId` modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="e3647-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="e3647-114">Po volání metody [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , modul runtime používá identifikátor k určení, zda byl obsah `IStream` namapován.</span><span class="sxs-lookup"><span data-stu-id="e3647-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="e3647-115">V takovém případě modul runtime načte existující kopii místo přemapování datového proudu.</span><span class="sxs-lookup"><span data-stu-id="e3647-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="e3647-116">Modul runtime používá tento identifikátor také jako vyhledávací klíč pro datové proudy, které jsou vráceny z volání metody `IHostAssemblyStore::ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e3647-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="e3647-117">Proto musí být identifikátor jedinečný pro požadavky modulů i pro požadavky na sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3647-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3647-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3647-118">Requirements</span></span>  
 <span data-ttu-id="e3647-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3647-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3647-120">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="e3647-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e3647-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3647-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3647-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3647-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3647-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3647-123">See also</span></span>

- [<span data-ttu-id="e3647-124">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="e3647-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="e3647-125">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="e3647-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="e3647-126">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3647-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e3647-127">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3647-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e3647-128">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3647-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
