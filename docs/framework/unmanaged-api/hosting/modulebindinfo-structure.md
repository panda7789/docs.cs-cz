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
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006750"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="dc58e-102">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="dc58e-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="dc58e-103">Obsahuje podrobné informace o odkazovaném modulu a sestavení, které ho obsahuje.</span><span class="sxs-lookup"><span data-stu-id="dc58e-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc58e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc58e-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="dc58e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dc58e-105">Members</span></span>  
  
|<span data-ttu-id="dc58e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dc58e-106">Member</span></span>|<span data-ttu-id="dc58e-107">Description</span><span class="sxs-lookup"><span data-stu-id="dc58e-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="dc58e-108">Jedinečný identifikátor `IStream` , který je vrácen voláním metody [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) , ze které má být načten odkazovaný modul.</span><span class="sxs-lookup"><span data-stu-id="dc58e-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="dc58e-109">Jedinečný identifikátor pro sestavení, které obsahuje odkazovaný modul.</span><span class="sxs-lookup"><span data-stu-id="dc58e-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="dc58e-110">Název odkazovaného modulu</span><span class="sxs-lookup"><span data-stu-id="dc58e-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc58e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc58e-111">Remarks</span></span>  
 <span data-ttu-id="dc58e-112">`ModuleBindInfo`je předán jako parametr do `IHostAssemblyStore::ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="dc58e-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="dc58e-113">Hostitel dodá jedinečný identifikátor modulu `dwAppDomainId` CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="dc58e-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="dc58e-114">Po volání metody [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) , modul runtime používá identifikátor k určení, zda `IStream` byl obsah namapovaný.</span><span class="sxs-lookup"><span data-stu-id="dc58e-114">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="dc58e-115">V takovém případě modul runtime načte existující kopii místo přemapování datového proudu.</span><span class="sxs-lookup"><span data-stu-id="dc58e-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="dc58e-116">Modul runtime používá tento identifikátor také jako vyhledávací klíč pro datové proudy, které jsou vráceny z volání `IHostAssemblyStore::ProvideAssembly` metody.</span><span class="sxs-lookup"><span data-stu-id="dc58e-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="dc58e-117">Proto musí být identifikátor jedinečný pro požadavky modulů i pro požadavky na sestavení.</span><span class="sxs-lookup"><span data-stu-id="dc58e-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc58e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc58e-118">Requirements</span></span>  
 <span data-ttu-id="dc58e-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc58e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc58e-120">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="dc58e-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="dc58e-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc58e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc58e-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc58e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc58e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc58e-123">See also</span></span>

- [<span data-ttu-id="dc58e-124">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="dc58e-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="dc58e-125">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="dc58e-125">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="dc58e-126">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc58e-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="dc58e-127">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc58e-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="dc58e-128">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc58e-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
