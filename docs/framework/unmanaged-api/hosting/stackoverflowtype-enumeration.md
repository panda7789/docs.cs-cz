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
ms.openlocfilehash: 64312398c95a33c2bbe136b1c4d03c06cb09aeef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="1fdaf-102">StackOverflowType – výčet</span><span class="sxs-lookup"><span data-stu-id="1fdaf-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="1fdaf-103">Obsahuje hodnoty, které označují základní příčinu události přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1fdaf-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fdaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fdaf-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="1fdaf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1fdaf-105">Members</span></span>  
  
|<span data-ttu-id="1fdaf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1fdaf-106">Member</span></span>|<span data-ttu-id="1fdaf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1fdaf-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="1fdaf-108">Spouštěcí modul způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1fdaf-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="1fdaf-109">Spravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1fdaf-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="1fdaf-110">Nespravovaný kód způsobila přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1fdaf-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fdaf-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fdaf-111">Remarks</span></span>  
 <span data-ttu-id="1fdaf-112">Tato informace je předána na hostitele pomocí volání [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="1fdaf-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fdaf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fdaf-113">Requirements</span></span>  
 <span data-ttu-id="1fdaf-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fdaf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fdaf-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1fdaf-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fdaf-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1fdaf-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fdaf-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fdaf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fdaf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fdaf-118">See Also</span></span>  
 [<span data-ttu-id="1fdaf-119">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="1fdaf-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
