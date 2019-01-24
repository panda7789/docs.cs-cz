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
ms.openlocfilehash: 97aded59f880412a6a26e7e3d664c50ff1c2f103
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557406"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="f7c35-102">MALLOC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="f7c35-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="f7c35-103">Obsahuje hodnoty, které určují vlastnosti paměti, které je právě přiděleno.</span><span class="sxs-lookup"><span data-stu-id="f7c35-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7c35-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="f7c35-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f7c35-105">Members</span></span>  
  
|<span data-ttu-id="f7c35-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f7c35-106">Member</span></span>|<span data-ttu-id="f7c35-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f7c35-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="f7c35-108">Přidělené paměti může obsahovat spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f7c35-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="f7c35-109">Přidělená paměť je bezpečná pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="f7c35-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="f7c35-110">To znamená, že paměť je přístupný prostřednictvím více vláken bez jakékoli synchronizace.</span><span class="sxs-lookup"><span data-stu-id="f7c35-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="f7c35-111">Pokud není tento příznak nastaven, volání objektu se musí serializovat.</span><span class="sxs-lookup"><span data-stu-id="f7c35-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7c35-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7c35-112">Requirements</span></span>  
 <span data-ttu-id="f7c35-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c35-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c35-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7c35-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7c35-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7c35-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7c35-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c35-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c35-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7c35-117">See also</span></span>
- [<span data-ttu-id="f7c35-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="f7c35-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
