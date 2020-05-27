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
ms.openlocfilehash: 630fe4e79b369bfdefc19be72780f1893090895e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008453"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="ff452-102">MALLOC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="ff452-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="ff452-103">Obsahuje hodnoty, které určují charakteristiky přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="ff452-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff452-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff452-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ff452-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ff452-105">Members</span></span>  
  
|<span data-ttu-id="ff452-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ff452-106">Member</span></span>|<span data-ttu-id="ff452-107">Description</span><span class="sxs-lookup"><span data-stu-id="ff452-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="ff452-108">Přidělená paměť může obsahovat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="ff452-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="ff452-109">Přidělená paměť je bezpečná pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="ff452-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="ff452-110">To znamená, že k paměti může být přistup více vlákny bez jakékoli synchronizace.</span><span class="sxs-lookup"><span data-stu-id="ff452-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="ff452-111">Pokud tento příznak není nastaven, volání objektu musí být serializována.</span><span class="sxs-lookup"><span data-stu-id="ff452-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff452-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff452-112">Requirements</span></span>  
 <span data-ttu-id="ff452-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff452-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff452-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff452-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff452-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ff452-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff452-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff452-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff452-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff452-117">See also</span></span>

- [<span data-ttu-id="ff452-118">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="ff452-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
