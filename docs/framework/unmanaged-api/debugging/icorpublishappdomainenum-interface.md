---
title: ICorPublishAppDomainEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790667"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="75d0e-102">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75d0e-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="75d0e-103">Podtřída rozhraní [ICorPublishEnum](icorpublishenum-interface.md) , která poskytuje metody pro procházení kolekce objektů [ICorPublishAppDomain](icorpublishappdomain-interface.md) , které aktuálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="75d0e-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75d0e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="75d0e-104">Methods</span></span>  
  
|<span data-ttu-id="75d0e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="75d0e-105">Method</span></span>|<span data-ttu-id="75d0e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="75d0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75d0e-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="75d0e-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="75d0e-108">Získá zadaný počet instancí `ICorPublishAppDomain` z kolekce počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="75d0e-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75d0e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75d0e-109">Remarks</span></span>  
 <span data-ttu-id="75d0e-110">Rozhraní `ICorPublishAppDomainEnum` implementuje metody abstraktního rozhraní [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="75d0e-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75d0e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75d0e-111">Requirements</span></span>  
 <span data-ttu-id="75d0e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75d0e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75d0e-113">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="75d0e-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="75d0e-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="75d0e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75d0e-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75d0e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d0e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75d0e-116">See also</span></span>

- [<span data-ttu-id="75d0e-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="75d0e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="75d0e-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="75d0e-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
