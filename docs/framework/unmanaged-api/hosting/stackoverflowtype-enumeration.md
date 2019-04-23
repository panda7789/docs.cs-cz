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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8541ea7b614ff4a6ca666f0e2549a7f50e190192
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135873"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="3191d-102">StackOverflowType – výčet</span><span class="sxs-lookup"><span data-stu-id="3191d-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="3191d-103">Obsahuje hodnoty, které označují základní příčiny událost přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3191d-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3191d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3191d-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="3191d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3191d-105">Members</span></span>  
  
|<span data-ttu-id="3191d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3191d-106">Member</span></span>|<span data-ttu-id="3191d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3191d-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="3191d-108">Prováděcí modul způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3191d-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="3191d-109">Spravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3191d-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="3191d-110">Nespravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3191d-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3191d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3191d-111">Remarks</span></span>  
 <span data-ttu-id="3191d-112">Tyto informace se předává k hostiteli volání [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3191d-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3191d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3191d-113">Requirements</span></span>  
 <span data-ttu-id="3191d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3191d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3191d-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3191d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3191d-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3191d-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3191d-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3191d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3191d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3191d-118">See also</span></span>

- [<span data-ttu-id="3191d-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="3191d-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
