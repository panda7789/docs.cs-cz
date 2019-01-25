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
ms.openlocfilehash: 1c2b383abdc67546749867de154a00fda244b3ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660018"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="53a56-102">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53a56-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="53a56-103">Spravuje seznam sestavení, která jsou načtena modulem common language runtime (CLR) a není hostitelem.</span><span class="sxs-lookup"><span data-stu-id="53a56-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53a56-104">Metody</span><span class="sxs-lookup"><span data-stu-id="53a56-104">Methods</span></span>  
  
|<span data-ttu-id="53a56-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="53a56-105">Method</span></span>|<span data-ttu-id="53a56-106">Popis</span><span class="sxs-lookup"><span data-stu-id="53a56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53a56-107">IsAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="53a56-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="53a56-108">Získá hodnotu určující, zda zadaný ukazatel odkazuje na sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="53a56-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="53a56-109">IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="53a56-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="53a56-110">Získá hodnotu určující, zda zadaný název odpovídá názvu sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="53a56-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53a56-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53a56-111">Remarks</span></span>  
 <span data-ttu-id="53a56-112">Volání [iclrassemblyidentitymanager::getclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) metodu k získání ukazatele na instanci `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="53a56-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53a56-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53a56-113">Requirements</span></span>  
 <span data-ttu-id="53a56-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53a56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53a56-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53a56-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53a56-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53a56-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53a56-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53a56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a56-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53a56-118">See also</span></span>
- [<span data-ttu-id="53a56-119">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53a56-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="53a56-120">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53a56-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="53a56-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="53a56-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
