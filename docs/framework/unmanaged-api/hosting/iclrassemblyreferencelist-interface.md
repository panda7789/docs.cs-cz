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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43c40e833e3a250239e9e90667196a2a74a96e0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187652"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="cfba3-102">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfba3-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="cfba3-103">Spravuje seznam sestavení, která jsou načtena modulem common language runtime (CLR) a není hostitelem.</span><span class="sxs-lookup"><span data-stu-id="cfba3-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfba3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cfba3-104">Methods</span></span>  
  
|<span data-ttu-id="cfba3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cfba3-105">Method</span></span>|<span data-ttu-id="cfba3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cfba3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfba3-107">IsAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="cfba3-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="cfba3-108">Získá hodnotu určující, zda zadaný ukazatel odkazuje na sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="cfba3-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="cfba3-109">IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="cfba3-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="cfba3-110">Získá hodnotu určující, zda zadaný název odpovídá názvu sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="cfba3-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfba3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfba3-111">Remarks</span></span>  
 <span data-ttu-id="cfba3-112">Volání [iclrassemblyidentitymanager::getclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodu k získání ukazatele na instanci `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="cfba3-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfba3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfba3-113">Requirements</span></span>  
 <span data-ttu-id="cfba3-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfba3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfba3-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cfba3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cfba3-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cfba3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cfba3-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cfba3-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cfba3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfba3-118">See also</span></span>

- [<span data-ttu-id="cfba3-119">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfba3-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="cfba3-120">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfba3-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="cfba3-121">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="cfba3-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
