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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777959"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="3a382-102">StackOverflowType – výčet</span><span class="sxs-lookup"><span data-stu-id="3a382-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="3a382-103">Obsahuje hodnoty, které označují základní příčiny událost přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3a382-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a382-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a382-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="3a382-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3a382-105">Members</span></span>  
  
|<span data-ttu-id="3a382-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3a382-106">Member</span></span>|<span data-ttu-id="3a382-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3a382-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="3a382-108">Prováděcí modul způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3a382-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="3a382-109">Spravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3a382-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="3a382-110">Nespravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3a382-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a382-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a382-111">Remarks</span></span>  
 <span data-ttu-id="3a382-112">Tyto informace se předává k hostiteli volání [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3a382-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a382-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a382-113">Requirements</span></span>  
 <span data-ttu-id="3a382-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a382-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a382-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a382-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a382-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a382-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a382-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a382-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a382-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a382-118">See also</span></span>

- [<span data-ttu-id="3a382-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="3a382-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
