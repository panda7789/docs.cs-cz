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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616915"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="bbbc0-102">AssemblyBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="bbbc0-102">AssemblyBindInfo Structure</span></span>
<span data-ttu-id="bbbc0-103">Poskytuje podrobné informace o odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-103">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbbc0-104">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="bbbc0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bbbc0-105">Members</span></span>  
  
|<span data-ttu-id="bbbc0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bbbc0-106">Member</span></span>|<span data-ttu-id="bbbc0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bbbc0-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="bbbc0-108">Jedinečný identifikátor `IStream` vrácený voláním [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md), ze kterého má být načteno odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-108">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="bbbc0-109">Jedinečný identifikátor odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-109">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="bbbc0-110">Identifikátor odkazovaného sestavení po použití všech hodnot zásad vazby</span><span class="sxs-lookup"><span data-stu-id="bbbc0-110">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="bbbc0-111">Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) určujících, které zásady správy verzí (pokud existují) by měly být aplikovány na odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-111">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbbc0-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbbc0-112">Remarks</span></span>  
 <span data-ttu-id="bbbc0-113">Hostitel dodá jedinečný identifikátor modulu `dwAppDomainId` CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="bbbc0-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="bbbc0-114">Po volání `IHostAssemblyStore::ProvideAssembly` vrátí modul runtime identifikátor, který určí, zda `IStream` byl obsah namapovaný.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-114">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="bbbc0-115">V takovém případě modul runtime načte existující kopii místo přemapování datového proudu.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="bbbc0-116">Modul runtime používá tento identifikátor také jako vyhledávací klíč pro proudy vracené z volání do [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="bbbc0-116">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="bbbc0-117">Proto musí být identifikátor jedinečný pro požadavky na modul a požadavky na sestavení.</span><span class="sxs-lookup"><span data-stu-id="bbbc0-117">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbbc0-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbbc0-118">Requirements</span></span>  
 <span data-ttu-id="bbbc0-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbbc0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbbc0-120">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="bbbc0-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="bbbc0-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bbbc0-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbbc0-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbbc0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbc0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbbc0-123">See also</span></span>

- [<span data-ttu-id="bbbc0-124">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="bbbc0-124">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="bbbc0-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbc0-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="bbbc0-126">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbc0-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bbbc0-127">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbc0-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="bbbc0-128">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbbc0-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="bbbc0-129">ModuleBindInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="bbbc0-129">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
