---
title: "CorSaveSize – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSaveSize
helpviewer_keywords: CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34d4d42c7cf385bca77de37dce52689778aa5b1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="ff6c5-102">CorSaveSize – výčet</span><span class="sxs-lookup"><span data-stu-id="ff6c5-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="ff6c5-103">Obsahuje hodnoty označující úroveň přesnost potřebné při dotazování na velikost uložení operace.</span><span class="sxs-lookup"><span data-stu-id="ff6c5-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff6c5-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="ff6c5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ff6c5-105">Members</span></span>  
  
|<span data-ttu-id="ff6c5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ff6c5-106">Member</span></span>|<span data-ttu-id="ff6c5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ff6c5-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="ff6c5-108">Určuje, že návratová hodnota by měla být přesná.</span><span class="sxs-lookup"><span data-stu-id="ff6c5-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="ff6c5-109">Určuje, že návratová hodnota by měla odhadované.</span><span class="sxs-lookup"><span data-stu-id="ff6c5-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="ff6c5-110">Určuje, že má být odebrána discardable typy.</span><span class="sxs-lookup"><span data-stu-id="ff6c5-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff6c5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff6c5-111">Requirements</span></span>  
 <span data-ttu-id="ff6c5-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff6c5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff6c5-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ff6c5-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ff6c5-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff6c5-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff6c5-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff6c5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6c5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff6c5-116">See Also</span></span>  
 [<span data-ttu-id="ff6c5-117">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="ff6c5-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
