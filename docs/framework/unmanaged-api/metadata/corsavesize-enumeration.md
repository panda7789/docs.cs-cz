---
title: CorSaveSize – výčet
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 0f870d9d7d1bc292b213d690df508a6c28bac2ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450097"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="7d438-102">CorSaveSize – výčet</span><span class="sxs-lookup"><span data-stu-id="7d438-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="7d438-103">Obsahuje hodnoty určující úroveň přesnosti požadovanou při dotazování na velikost operace uložení.</span><span class="sxs-lookup"><span data-stu-id="7d438-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d438-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d438-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="7d438-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7d438-105">Members</span></span>  
  
|<span data-ttu-id="7d438-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7d438-106">Member</span></span>|<span data-ttu-id="7d438-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7d438-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="7d438-108">Určuje, že návratová hodnota by měla být přesně.</span><span class="sxs-lookup"><span data-stu-id="7d438-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="7d438-109">Určuje, že návratová hodnota by měla být odhadnuta.</span><span class="sxs-lookup"><span data-stu-id="7d438-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="7d438-110">Určuje, že by měly být odebrány typy, které by se měly odstranit.</span><span class="sxs-lookup"><span data-stu-id="7d438-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d438-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d438-111">Requirements</span></span>  
 <span data-ttu-id="7d438-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d438-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d438-113">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7d438-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7d438-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7d438-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7d438-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d438-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d438-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d438-116">See also</span></span>

- [<span data-ttu-id="7d438-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="7d438-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
