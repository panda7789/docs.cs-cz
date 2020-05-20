---
title: ECustomDumpFlavor – výčet
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 9b4c1187945b4c243375a3096c3a8a3b22599aef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616278"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="274d3-102">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="274d3-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="274d3-103">Obsahuje hodnoty, které určují, které položky se mají zahrnout do vlastní podmnožiny výpisu haldy při vytváření sestav chyb.</span><span class="sxs-lookup"><span data-stu-id="274d3-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="274d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="274d3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="274d3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="274d3-105">Members</span></span>  
  
|<span data-ttu-id="274d3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="274d3-106">Member</span></span>|<span data-ttu-id="274d3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="274d3-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="274d3-108">Určuje, že by se měl spustit výpis vlastní haldy jako s minimálním výpisem a zahrnout další data určená všemi instancemi [CustomDumpItem –](customdumpitem-structure.md) předanými do stejné metody.</span><span class="sxs-lookup"><span data-stu-id="274d3-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="274d3-109">Určuje, že by měl být ve vlastním výpisu haldy shromažďována všechna data běhového stavu, která nebyla dynamicky přidělena.</span><span class="sxs-lookup"><span data-stu-id="274d3-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="274d3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="274d3-110">Remarks</span></span>  
 <span data-ttu-id="274d3-111">Parametr typu `ECustomDumpFlavor` je předán metodě [ICLRErrorReportingManager:: BeginCustomDump –](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="274d3-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="274d3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="274d3-112">Requirements</span></span>  
 <span data-ttu-id="274d3-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="274d3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="274d3-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="274d3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="274d3-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="274d3-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="274d3-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="274d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="274d3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="274d3-117">See also</span></span>

- [<span data-ttu-id="274d3-118">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="274d3-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="274d3-119">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="274d3-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="274d3-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="274d3-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
