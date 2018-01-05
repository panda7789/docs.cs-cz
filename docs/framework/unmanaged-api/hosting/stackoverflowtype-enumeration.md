---
title: "StackOverflowType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowType
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowType
helpviewer_keywords: StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a04db61a16aeae24476fb0b191a3d2dc89743dee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="8e070-102">StackOverflowType – výčet</span><span class="sxs-lookup"><span data-stu-id="8e070-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="8e070-103">Obsahuje hodnoty, které označují základní příčinu události přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8e070-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e070-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="8e070-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8e070-105">Members</span></span>  
  
|<span data-ttu-id="8e070-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8e070-106">Member</span></span>|<span data-ttu-id="8e070-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8e070-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="8e070-108">Spouštěcí modul způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8e070-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="8e070-109">Spravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8e070-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="8e070-110">Nespravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8e070-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e070-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e070-111">Remarks</span></span>  
 <span data-ttu-id="8e070-112">Tato informace je předána na hostitele pomocí volání [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8e070-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e070-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e070-113">Requirements</span></span>  
 <span data-ttu-id="8e070-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e070-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e070-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e070-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e070-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e070-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e070-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e070-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e070-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e070-118">See Also</span></span>  
 [<span data-ttu-id="8e070-119">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="8e070-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
