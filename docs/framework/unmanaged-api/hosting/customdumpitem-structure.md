---
title: CustomDumpItem – struktura
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 930d56fcfe7cf0d2a128c2068e724b85a224b3fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568917"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="4a0ee-102">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="4a0ee-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="4a0ee-103">Popisuje položku, kterou chcete přidat do vlastní výpisu stavu systému v hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a0ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a0ee-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="4a0ee-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4a0ee-105">Members</span></span>  
  
|<span data-ttu-id="4a0ee-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4a0ee-106">Member</span></span>|<span data-ttu-id="4a0ee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4a0ee-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="4a0ee-108">[Ecustomdumpitemkind –](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) hodnotu, která určuje typ přidávané položky.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="4a0ee-109">Není v současné době nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-109">Not currently used.</span></span> <span data-ttu-id="4a0ee-110">Všechny položky přidané do sjednocení nesmí být větší než velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="4a0ee-111">Pokud `struct` je potřeba, musí přidělit samostatně a přejděte na to.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a0ee-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a0ee-112">Remarks</span></span>  
 <span data-ttu-id="4a0ee-113">[Iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="4a0ee-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a0ee-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a0ee-114">Requirements</span></span>  
 <span data-ttu-id="4a0ee-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a0ee-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a0ee-116">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="4a0ee-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4a0ee-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a0ee-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a0ee-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a0ee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0ee-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a0ee-119">See also</span></span>
- [<span data-ttu-id="4a0ee-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="4a0ee-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
