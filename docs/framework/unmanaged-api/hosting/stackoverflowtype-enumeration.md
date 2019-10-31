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
ms.openlocfilehash: f09c6bb79d7bd28f4d8b74237b6f343a07b79062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141480"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="c30cb-102">StackOverflowType – výčet</span><span class="sxs-lookup"><span data-stu-id="c30cb-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="c30cb-103">Obsahuje hodnoty, které indikují základní příčinu události přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c30cb-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c30cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c30cb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="c30cb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c30cb-105">Members</span></span>  
  
|<span data-ttu-id="c30cb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c30cb-106">Member</span></span>|<span data-ttu-id="c30cb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c30cb-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="c30cb-108">Přetečení zásobníku bylo způsobené prováděcím modulem.</span><span class="sxs-lookup"><span data-stu-id="c30cb-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="c30cb-109">Přetečení zásobníku bylo způsobeno spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c30cb-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="c30cb-110">Přetečení zásobníku bylo způsobeno nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c30cb-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c30cb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c30cb-111">Remarks</span></span>  
 <span data-ttu-id="c30cb-112">Tyto informace jsou předány hostiteli prostřednictvím volání metody [IActionOnCLREvent –::](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c30cb-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c30cb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c30cb-113">Requirements</span></span>  
 <span data-ttu-id="c30cb-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c30cb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c30cb-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c30cb-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c30cb-116">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c30cb-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c30cb-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c30cb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c30cb-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c30cb-118">See also</span></span>

- [<span data-ttu-id="c30cb-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="c30cb-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
