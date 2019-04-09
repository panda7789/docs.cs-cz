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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32f27d6c15a99282eee20d2563a4ca741238d846
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187396"
---
# <a name="iclrreferenceassemblyenum-interface"></a><span data-ttu-id="b8e3c-102">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8e3c-102">ICLRReferenceAssemblyEnum Interface</span></span>
<span data-ttu-id="b8e3c-103">Poskytuje metody, které umožňují hostitele k manipulaci s sadu sestavení odkazuje na soubor nebo datový proud pomocí data identitu sestavení, která je interní common language runtime (CLR), aniž by bylo nutné vytvořit nebo pochopit tyto identity.</span><span class="sxs-lookup"><span data-stu-id="b8e3c-103">Provides methods that allow the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the common language runtime (CLR), without needing to create or understand those identities.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8e3c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b8e3c-104">Methods</span></span>  
  
|<span data-ttu-id="b8e3c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b8e3c-105">Method</span></span>|<span data-ttu-id="b8e3c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b8e3c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8e3c-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="b8e3c-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-get-method.md)|<span data-ttu-id="b8e3c-108">Získá identitu sestavení u zadaného indexu.</span><span class="sxs-lookup"><span data-stu-id="b8e3c-108">Gets the assembly identity at the supplied index.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8e3c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8e3c-109">Requirements</span></span>  
 <span data-ttu-id="b8e3c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e3c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e3c-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8e3c-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8e3c-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8e3c-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b8e3c-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b8e3c-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8e3c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8e3c-114">See also</span></span>

- [<span data-ttu-id="b8e3c-115">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8e3c-115">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b8e3c-116">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8e3c-116">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b8e3c-117">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="b8e3c-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
