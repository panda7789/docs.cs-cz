---
title: StackOverflowType – výčet
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: f399d33dbe05cb5768aa45533ef30d28409e18e2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006464"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="c00c1-102">StackOverflowType – výčet</span><span class="sxs-lookup"><span data-stu-id="c00c1-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="c00c1-103">Obsahuje hodnoty, které indikují základní příčinu události přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c00c1-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c00c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c00c1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="c00c1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c00c1-105">Members</span></span>  
  
|<span data-ttu-id="c00c1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c00c1-106">Member</span></span>|<span data-ttu-id="c00c1-107">Description</span><span class="sxs-lookup"><span data-stu-id="c00c1-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="c00c1-108">Přetečení zásobníku bylo způsobené prováděcím modulem.</span><span class="sxs-lookup"><span data-stu-id="c00c1-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="c00c1-109">Přetečení zásobníku bylo způsobeno spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c00c1-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="c00c1-110">Přetečení zásobníku bylo způsobeno nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c00c1-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c00c1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c00c1-111">Remarks</span></span>  
 <span data-ttu-id="c00c1-112">Tyto informace jsou předány hostiteli prostřednictvím volání metody [IActionOnCLREvent –::](iactiononclrevent-onevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c00c1-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c00c1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c00c1-113">Requirements</span></span>  
 <span data-ttu-id="c00c1-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c00c1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c00c1-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c00c1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c00c1-116">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c00c1-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c00c1-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c00c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c00c1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c00c1-118">See also</span></span>

- [<span data-ttu-id="c00c1-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="c00c1-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
