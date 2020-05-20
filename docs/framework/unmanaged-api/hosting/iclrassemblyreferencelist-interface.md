---
title: ICLRAssemblyReferenceList – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f1aa40ef868bf6ff7730e01ab66a6fec58af1196
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615875"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="ca966-102">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca966-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="ca966-103">Spravuje seznam sestavení, která jsou načtena modulem CLR (Common Language Runtime), nikoli hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ca966-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca966-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca966-104">Methods</span></span>  
  
|<span data-ttu-id="ca966-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca966-105">Method</span></span>|<span data-ttu-id="ca966-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ca966-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca966-107">IsAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="ca966-107">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="ca966-108">Získá hodnotu, která označuje, zda zadaný ukazatel odkazuje na sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="ca966-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="ca966-109">IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="ca966-109">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="ca966-110">Získá hodnotu, která označuje, zda je zadaný název shodný s názvem sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="ca966-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca966-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca966-111">Remarks</span></span>  
 <span data-ttu-id="ca966-112">Voláním metody [ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList –](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) získá ukazatel na instanci `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="ca966-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca966-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca966-113">Requirements</span></span>  
 <span data-ttu-id="ca966-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca966-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca966-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ca966-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca966-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca966-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca966-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca966-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca966-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca966-118">See also</span></span>

- [<span data-ttu-id="ca966-119">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca966-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ca966-120">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca966-120">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="ca966-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ca966-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
