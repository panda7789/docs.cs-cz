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
ms.openlocfilehash: 13a4364244f7d0076d77d14c3e3ef161e3872bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176133"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="9247b-102">CorSaveSize – výčet</span><span class="sxs-lookup"><span data-stu-id="9247b-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="9247b-103">Obsahuje hodnoty označující úroveň přesnosti požadované při dotazování na velikost operace uložení.</span><span class="sxs-lookup"><span data-stu-id="9247b-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9247b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9247b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="9247b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9247b-105">Members</span></span>  
  
|<span data-ttu-id="9247b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9247b-106">Member</span></span>|<span data-ttu-id="9247b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9247b-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="9247b-108">Určuje, že vrácená hodnota by měla být přesná.</span><span class="sxs-lookup"><span data-stu-id="9247b-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="9247b-109">Určuje, že má být odhadnuta vrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="9247b-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="9247b-110">Určuje, že by měly být odebrány zahoditelné typy.</span><span class="sxs-lookup"><span data-stu-id="9247b-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9247b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9247b-111">Requirements</span></span>  
 <span data-ttu-id="9247b-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9247b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9247b-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9247b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9247b-114">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9247b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9247b-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9247b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9247b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9247b-116">See also</span></span>

- [<span data-ttu-id="9247b-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9247b-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
