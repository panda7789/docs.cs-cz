---
title: ICLRReferenceAssemblyEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum
helpviewer_keywords:
- ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: 8adbf092-c3ba-4bee-b25b-0de6e43a4ce5
topic_type:
- apiref
ms.openlocfilehash: 9797c419251127ef07a8c2bee22132c3c2b82e36
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703327"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="ab4bf-102">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab4bf-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="ab4bf-103">Poskytuje metody, které umožňují hostiteli manipulovat s množinou sestavení, na které odkazuje soubor nebo datový proud, pomocí dat identity sestavení, která jsou interní pro modul CLR (Common Language Runtime), a to bez nutnosti vytvářet nebo porozumět těmto identitám.</span><span class="sxs-lookup"><span data-stu-id="ab4bf-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab4bf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab4bf-104">Methods</span></span>  
  
|<span data-ttu-id="ab4bf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab4bf-105">Method</span></span>|<span data-ttu-id="ab4bf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ab4bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab4bf-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="ab4bf-107">Get Method</span></span>](iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="ab4bf-108">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="ab4bf-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab4bf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab4bf-109">Requirements</span></span>  
 <span data-ttu-id="ab4bf-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab4bf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab4bf-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ab4bf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab4bf-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ab4bf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab4bf-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab4bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4bf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab4bf-114">See also</span></span>

- [<span data-ttu-id="ab4bf-115">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab4bf-115">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ab4bf-116">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab4bf-116">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ab4bf-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ab4bf-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
