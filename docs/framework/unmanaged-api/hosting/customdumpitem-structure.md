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
ms.openlocfilehash: 05f5d3fbe05ad1e97a1ae61ed0496f314c4ec5cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765967"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="65bb7-102">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="65bb7-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="65bb7-103">Popisuje položku, kterou chcete přidat do vlastní výpisu stavu systému v hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="65bb7-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65bb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65bb7-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="65bb7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="65bb7-105">Members</span></span>  
  
|<span data-ttu-id="65bb7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="65bb7-106">Member</span></span>|<span data-ttu-id="65bb7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65bb7-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="65bb7-108">[Ecustomdumpitemkind –](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) hodnotu, která určuje typ přidávané položky.</span><span class="sxs-lookup"><span data-stu-id="65bb7-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="65bb7-109">Není v současné době nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="65bb7-109">Not currently used.</span></span> <span data-ttu-id="65bb7-110">Všechny položky přidané do sjednocení nesmí být větší než velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="65bb7-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="65bb7-111">Pokud `struct` je potřeba, musí přidělit samostatně a přejděte na to.</span><span class="sxs-lookup"><span data-stu-id="65bb7-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65bb7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65bb7-112">Remarks</span></span>  
 <span data-ttu-id="65bb7-113">[Iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="65bb7-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65bb7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65bb7-114">Requirements</span></span>  
 <span data-ttu-id="65bb7-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65bb7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65bb7-116">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="65bb7-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="65bb7-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65bb7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65bb7-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65bb7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65bb7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65bb7-119">See also</span></span>

- [<span data-ttu-id="65bb7-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="65bb7-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
