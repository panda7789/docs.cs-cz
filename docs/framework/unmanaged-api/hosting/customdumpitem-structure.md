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
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176471"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="0d77b-102">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="0d77b-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="0d77b-103">Popisuje položku, která má být přidána do vlastního výpisu chyb v hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="0d77b-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d77b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d77b-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="0d77b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0d77b-105">Members</span></span>  
  
|<span data-ttu-id="0d77b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0d77b-106">Member</span></span>|<span data-ttu-id="0d77b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0d77b-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="0d77b-108">Hodnota [ECustomDumpItemKind,](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) která označuje druh položky, která má být přidána.</span><span class="sxs-lookup"><span data-stu-id="0d77b-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="0d77b-109">Není aktuálně používán.</span><span class="sxs-lookup"><span data-stu-id="0d77b-109">Not currently used.</span></span> <span data-ttu-id="0d77b-110">Všechny položky přidané do unie nesmí být větší než velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="0d77b-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="0d77b-111">Pokud `struct` je požadováno, musíte ji přidělit samostatně a přejděte na něj.</span><span class="sxs-lookup"><span data-stu-id="0d77b-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d77b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d77b-112">Remarks</span></span>  
 <span data-ttu-id="0d77b-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr `CustomDumpItem`typu .</span><span class="sxs-lookup"><span data-stu-id="0d77b-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d77b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d77b-114">Requirements</span></span>  
 <span data-ttu-id="0d77b-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d77b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d77b-116">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0d77b-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0d77b-117">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d77b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d77b-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d77b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d77b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d77b-119">See also</span></span>

- [<span data-ttu-id="0d77b-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="0d77b-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
