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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bc1e788f6a55fa6441592141d3a2236a7a0e2d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701765"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="9ba04-102">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="9ba04-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="9ba04-103">Poskytuje podrobné informace o odkazovaného modulu a sestavení, který jej obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9ba04-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ba04-104">Syntax</span></span>  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="9ba04-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9ba04-105">Members</span></span>  
  
|<span data-ttu-id="9ba04-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9ba04-106">Member</span></span>|<span data-ttu-id="9ba04-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9ba04-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="9ba04-108">Jedinečný identifikátor `IStream` , který je vrácen voláním [ihostassemblystore::providemodule –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metoda, ze kterého má být načten odkazovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="9ba04-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="9ba04-109">Jedinečný identifikátor pro sestavení, které obsahuje odkazovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="9ba04-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="9ba04-110">Název odkazovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="9ba04-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ba04-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ba04-111">Remarks</span></span>  
 <span data-ttu-id="9ba04-112">`ModuleBindInfo` je předán jako parametr `IHostAssemblyStore::ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="9ba04-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="9ba04-113">Hostitel poskytuje jedinečný identifikátor `dwAppDomainId` do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9ba04-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="9ba04-114">Po volání [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda vrací výsledek, modul runtime používá identifikátoru k určení, zda obsah `IStream` byly namapovány.</span><span class="sxs-lookup"><span data-stu-id="9ba04-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="9ba04-115">Pokud ano, načte modul runtime stávající kopie spíše než přemapování datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9ba04-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="9ba04-116">Modul runtime také používá tento identifikátor jako vyhledávací klíč pro datové proudy, které jsou vráceny z volání `IHostAssemblyStore::ProvideAssembly` metody.</span><span class="sxs-lookup"><span data-stu-id="9ba04-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="9ba04-117">Proto identifikátoru musí být jedinečný pro modul požadavky i jako u žádosti o sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ba04-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ba04-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ba04-118">Requirements</span></span>  
 <span data-ttu-id="9ba04-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ba04-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba04-120">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="9ba04-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9ba04-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ba04-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ba04-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba04-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba04-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ba04-123">See also</span></span>
- [<span data-ttu-id="9ba04-124">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="9ba04-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="9ba04-125">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="9ba04-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="9ba04-126">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ba04-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9ba04-127">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ba04-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9ba04-128">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ba04-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
