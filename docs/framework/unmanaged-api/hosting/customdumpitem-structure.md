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
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616434"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="17209-102">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="17209-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="17209-103">Popisuje položku, která se má přidat do vlastního výpisu paměti při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="17209-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17209-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17209-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="17209-105">Členové</span><span class="sxs-lookup"><span data-stu-id="17209-105">Members</span></span>  
  
|<span data-ttu-id="17209-106">Člen</span><span class="sxs-lookup"><span data-stu-id="17209-106">Member</span></span>|<span data-ttu-id="17209-107">Popis</span><span class="sxs-lookup"><span data-stu-id="17209-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="17209-108">Hodnota [ECustomDumpItemKind –](ecustomdumpitemkind-enumeration.md) , která určuje druh položky, která má být přidána.</span><span class="sxs-lookup"><span data-stu-id="17209-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="17209-109">Aktuálně se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="17209-109">Not currently used.</span></span> <span data-ttu-id="17209-110">Všechny položky přidané do sjednocení nesmí být větší než velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="17209-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="17209-111">Pokud `struct` je vyžadován, je nutné jej přidělit samostatně a odkazovat na něj.</span><span class="sxs-lookup"><span data-stu-id="17209-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17209-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17209-112">Remarks</span></span>  
 <span data-ttu-id="17209-113">[ICLRErrorReportingManager:: BeginCustomDump –](iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="17209-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17209-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17209-114">Requirements</span></span>  
 <span data-ttu-id="17209-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17209-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17209-116">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="17209-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="17209-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17209-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17209-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17209-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17209-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="17209-119">See also</span></span>

- [<span data-ttu-id="17209-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="17209-120">Hosting Structures</span></span>](hosting-structures.md)
