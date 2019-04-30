---
title: AssemblyBindInfo – struktura
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce79987c7fcf45b8d10dcc4613e053ee735941de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946823"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="c78f3-102">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c78f3-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="c78f3-103">Poskytuje podrobné informace o odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="c78f3-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c78f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c78f3-104">Syntax</span></span>  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="c78f3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c78f3-105">Members</span></span>  
  
|<span data-ttu-id="c78f3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c78f3-106">Member</span></span>|<span data-ttu-id="c78f3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c78f3-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="c78f3-108">Jedinečný identifikátor `IStream` vrácený voláním [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), ze které má odkazované sestavení má být načten.</span><span class="sxs-lookup"><span data-stu-id="c78f3-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="c78f3-109">Jedinečný identifikátor odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="c78f3-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="c78f3-110">Identifikátor odkazovaného sestavení po použití hodnoty zásad žádné vazby.</span><span class="sxs-lookup"><span data-stu-id="c78f3-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="c78f3-111">Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které označují, které zásady správy verzí, pokud existuje, bude použito k odkazovanému sestavení.</span><span class="sxs-lookup"><span data-stu-id="c78f3-111">One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c78f3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c78f3-112">Remarks</span></span>  
 <span data-ttu-id="c78f3-113">Hostitel poskytuje jedinečný identifikátor `dwAppDomainId` do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c78f3-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="c78f3-114">Po volání `IHostAssemblyStore::ProvideAssembly` vrátí, modul runtime používá identifikátoru k určení, zda obsah `IStream` nebyly namapovány.</span><span class="sxs-lookup"><span data-stu-id="c78f3-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="c78f3-115">Pokud ano, načte modul runtime stávající kopie spíše než přemapování datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c78f3-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="c78f3-116">Modul runtime také používá tento identifikátor jako vyhledávací klíč pro datové proudy vrácené z volání [ihostassemblystore::providemodule –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="c78f3-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="c78f3-117">Proto musí být identifikátor jedinečný modul požadavky a požadavky na sestavení.</span><span class="sxs-lookup"><span data-stu-id="c78f3-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c78f3-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c78f3-118">Requirements</span></span>  
 <span data-ttu-id="c78f3-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c78f3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c78f3-120">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c78f3-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c78f3-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c78f3-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c78f3-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c78f3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c78f3-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c78f3-123">See also</span></span>

- [<span data-ttu-id="c78f3-124">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="c78f3-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="c78f3-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c78f3-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c78f3-126">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c78f3-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c78f3-127">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c78f3-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="c78f3-128">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c78f3-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="c78f3-129">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c78f3-129">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
