---
title: MALLOC_TYPE – výčet
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 695f69c8d9c3a295a705971743733339cf8aab13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765216"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="1e846-102">MALLOC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="1e846-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="1e846-103">Obsahuje hodnoty, které určují vlastnosti paměti, které je právě přiděleno.</span><span class="sxs-lookup"><span data-stu-id="1e846-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e846-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e846-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="1e846-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1e846-105">Members</span></span>  
  
|<span data-ttu-id="1e846-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1e846-106">Member</span></span>|<span data-ttu-id="1e846-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1e846-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="1e846-108">Přidělené paměti může obsahovat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="1e846-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="1e846-109">Přidělená paměť je bezpečná pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="1e846-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="1e846-110">To znamená, že paměť je přístupný prostřednictvím více vláken bez jakékoli synchronizace.</span><span class="sxs-lookup"><span data-stu-id="1e846-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="1e846-111">Pokud není tento příznak nastaven, volání objektu se musí serializovat.</span><span class="sxs-lookup"><span data-stu-id="1e846-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e846-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e846-112">Requirements</span></span>  
 <span data-ttu-id="1e846-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e846-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e846-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e846-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e846-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e846-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e846-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e846-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e846-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e846-117">See also</span></span>

- [<span data-ttu-id="1e846-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="1e846-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
