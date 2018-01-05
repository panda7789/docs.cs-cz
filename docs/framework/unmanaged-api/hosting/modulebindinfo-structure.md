---
title: "ModuleBindInfo – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="60f6b-102">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="60f6b-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="60f6b-103">Poskytuje podrobné informace o odkazovaného modulu a sestavení, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="60f6b-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60f6b-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="60f6b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="60f6b-105">Members</span></span>  
  
|<span data-ttu-id="60f6b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="60f6b-106">Member</span></span>|<span data-ttu-id="60f6b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="60f6b-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="60f6b-108">Jedinečný identifikátor `IStream` , je vrácen rutinou volání [ihostassemblystore::providemodule –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metoda, ze kterého má být načten odkazovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="60f6b-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="60f6b-109">Jedinečný identifikátor pro sestavení, které obsahuje odkazovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="60f6b-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="60f6b-110">Název odkazovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="60f6b-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60f6b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60f6b-111">Remarks</span></span>  
 <span data-ttu-id="60f6b-112">`ModuleBindInfo`byla předána jako parametr pro `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="60f6b-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="60f6b-113">Hostitel poskytuje jedinečný identifikátor `dwAppDomainId` do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="60f6b-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="60f6b-114">Po volání [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda vrátí hodnotu, modul runtime používá k určení identifikátor zda obsah `IStream` namapované.</span><span class="sxs-lookup"><span data-stu-id="60f6b-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="60f6b-115">Pokud ano, načte modul runtime existující kopie místo přemapování datového proudu.</span><span class="sxs-lookup"><span data-stu-id="60f6b-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="60f6b-116">Modul runtime také používá tento identifikátor jako klíč vyhledávání pro datové proudy, které jsou vráceny z volání `IHostAssemblyStore::ProvideAssembly` metoda.</span><span class="sxs-lookup"><span data-stu-id="60f6b-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="60f6b-117">Proto musí být jedinečný pro požadavky modulu také jako požadavků sestavení na identifikátor.</span><span class="sxs-lookup"><span data-stu-id="60f6b-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f6b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60f6b-118">Requirements</span></span>  
 <span data-ttu-id="60f6b-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f6b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f6b-120">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="60f6b-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="60f6b-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60f6b-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60f6b-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f6b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f6b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="60f6b-123">See Also</span></span>  
 [<span data-ttu-id="60f6b-124">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="60f6b-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="60f6b-125">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="60f6b-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [<span data-ttu-id="60f6b-126">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60f6b-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="60f6b-127">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60f6b-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="60f6b-128">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60f6b-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
