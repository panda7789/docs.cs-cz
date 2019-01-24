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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f756e8688299fbe9d53822851be83703f4aa6348
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550627"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="70946-102">CorSaveSize – výčet</span><span class="sxs-lookup"><span data-stu-id="70946-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="70946-103">Obsahuje hodnoty určující úroveň přesnosti se vyžaduje při dotazování na velikost uložení operace.</span><span class="sxs-lookup"><span data-stu-id="70946-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70946-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70946-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="70946-105">Členové</span><span class="sxs-lookup"><span data-stu-id="70946-105">Members</span></span>  
  
|<span data-ttu-id="70946-106">Člen</span><span class="sxs-lookup"><span data-stu-id="70946-106">Member</span></span>|<span data-ttu-id="70946-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70946-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="70946-108">Určuje, že návratová hodnota by měla být přesné.</span><span class="sxs-lookup"><span data-stu-id="70946-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="70946-109">Určuje, že návratová hodnota by měla odhad.</span><span class="sxs-lookup"><span data-stu-id="70946-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="70946-110">Určuje, zda má být odebrána discardable typy.</span><span class="sxs-lookup"><span data-stu-id="70946-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70946-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70946-111">Requirements</span></span>  
 <span data-ttu-id="70946-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70946-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70946-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="70946-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="70946-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70946-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70946-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70946-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70946-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70946-116">See also</span></span>
- [<span data-ttu-id="70946-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="70946-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
