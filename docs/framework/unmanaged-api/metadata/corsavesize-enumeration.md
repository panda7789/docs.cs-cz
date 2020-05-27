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
ms.openlocfilehash: 22a7f87a5803dc185052a5ce7ed427eff9f8fb18
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009181"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="e757e-102">CorSaveSize – výčet</span><span class="sxs-lookup"><span data-stu-id="e757e-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="e757e-103">Obsahuje hodnoty určující úroveň přesnosti požadovanou při dotazování na velikost operace uložení.</span><span class="sxs-lookup"><span data-stu-id="e757e-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e757e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e757e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="e757e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e757e-105">Members</span></span>  
  
|<span data-ttu-id="e757e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e757e-106">Member</span></span>|<span data-ttu-id="e757e-107">Description</span><span class="sxs-lookup"><span data-stu-id="e757e-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="e757e-108">Určuje, že návratová hodnota by měla být přesně.</span><span class="sxs-lookup"><span data-stu-id="e757e-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="e757e-109">Určuje, že návratová hodnota by měla být odhadnuta.</span><span class="sxs-lookup"><span data-stu-id="e757e-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="e757e-110">Určuje, že by měly být odebrány typy, které by se měly odstranit.</span><span class="sxs-lookup"><span data-stu-id="e757e-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e757e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e757e-111">Requirements</span></span>  
 <span data-ttu-id="e757e-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e757e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e757e-113">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e757e-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e757e-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e757e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e757e-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e757e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e757e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e757e-116">See also</span></span>

- [<span data-ttu-id="e757e-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="e757e-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
