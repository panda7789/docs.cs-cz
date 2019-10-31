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
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090826"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="145d3-102">MALLOC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="145d3-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="145d3-103">Obsahuje hodnoty, které určují charakteristiky přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="145d3-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="145d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="145d3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="145d3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="145d3-105">Members</span></span>  
  
|<span data-ttu-id="145d3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="145d3-106">Member</span></span>|<span data-ttu-id="145d3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="145d3-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="145d3-108">Přidělená paměť může obsahovat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="145d3-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="145d3-109">Přidělená paměť je bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="145d3-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="145d3-110">To znamená, že k paměti může být přistup více vlákny bez jakékoli synchronizace.</span><span class="sxs-lookup"><span data-stu-id="145d3-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="145d3-111">Pokud tento příznak není nastaven, volání objektu musí být serializována.</span><span class="sxs-lookup"><span data-stu-id="145d3-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="145d3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="145d3-112">Requirements</span></span>  
 <span data-ttu-id="145d3-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="145d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="145d3-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="145d3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="145d3-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="145d3-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="145d3-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="145d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145d3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="145d3-117">See also</span></span>

- [<span data-ttu-id="145d3-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="145d3-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
