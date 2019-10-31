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
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138285"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="b764e-102">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="b764e-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="b764e-103">Popisuje položku, která se má přidat do vlastního výpisu paměti při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="b764e-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b764e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b764e-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="b764e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b764e-105">Members</span></span>  
  
|<span data-ttu-id="b764e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b764e-106">Member</span></span>|<span data-ttu-id="b764e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b764e-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="b764e-108">Hodnota [ECustomDumpItemKind –](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) , která určuje druh položky, která má být přidána.</span><span class="sxs-lookup"><span data-stu-id="b764e-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="b764e-109">Aktuálně se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b764e-109">Not currently used.</span></span> <span data-ttu-id="b764e-110">Všechny položky přidané do sjednocení nesmí být větší než velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="b764e-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="b764e-111">Pokud je vyžadován `struct`, je nutné jej přidělit samostatně a odkazovat na něj.</span><span class="sxs-lookup"><span data-stu-id="b764e-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b764e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b764e-112">Remarks</span></span>  
 <span data-ttu-id="b764e-113">[ICLRErrorReportingManager:: BeginCustomDump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="b764e-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b764e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b764e-114">Requirements</span></span>  
 <span data-ttu-id="b764e-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b764e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b764e-116">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="b764e-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b764e-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b764e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b764e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b764e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b764e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b764e-119">See also</span></span>

- [<span data-ttu-id="b764e-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="b764e-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
