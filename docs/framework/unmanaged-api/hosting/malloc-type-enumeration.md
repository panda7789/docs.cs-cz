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
ms.openlocfilehash: 2c5e970a1677b1e43821cce9985e32ebd0726686
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442537"
---
# <a name="malloctype-enumeration"></a><span data-ttu-id="f6884-102">MALLOC_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="f6884-102">MALLOC_TYPE Enumeration</span></span>
<span data-ttu-id="f6884-103">Obsahuje hodnoty, které určují charakteristiky paměti, které je právě přiděleno.</span><span class="sxs-lookup"><span data-stu-id="f6884-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6884-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6884-104">Syntax</span></span>  
  
```  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="f6884-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f6884-105">Members</span></span>  
  
|<span data-ttu-id="f6884-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f6884-106">Member</span></span>|<span data-ttu-id="f6884-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f6884-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="f6884-108">Přidělené paměti může obsahovat spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="f6884-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="f6884-109">Přidělenou paměť je bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f6884-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="f6884-110">To znamená paměť přístupná pomocí více vláken bez jakékoli synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="f6884-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="f6884-111">Pokud není nastavený tento příznak, musí být serializované volání na objekt.</span><span class="sxs-lookup"><span data-stu-id="f6884-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6884-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6884-112">Requirements</span></span>  
 <span data-ttu-id="f6884-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6884-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6884-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6884-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6884-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6884-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6884-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6884-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6884-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6884-117">See Also</span></span>  
 [<span data-ttu-id="f6884-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="f6884-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
