---
title: "CLR_DEBUGGING_VERSION – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98124b7b9efb2c92ebee6b6e99f73edc6cf173a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="0bb65-102">CLR_DEBUGGING_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="0bb65-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="0bb65-103">Definuje verze produktu common language runtime (CLR) pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="0bb65-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bb65-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="0bb65-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0bb65-105">Members</span></span>  
  
|<span data-ttu-id="0bb65-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0bb65-106">Member</span></span>|<span data-ttu-id="0bb65-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0bb65-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="0bb65-108">Číslo verze struktura</span><span class="sxs-lookup"><span data-stu-id="0bb65-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="0bb65-109">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="0bb65-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="0bb65-110">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="0bb65-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="0bb65-111">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="0bb65-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="0bb65-112">Číslo revize.</span><span class="sxs-lookup"><span data-stu-id="0bb65-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb65-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bb65-113">Remarks</span></span>  
 <span data-ttu-id="0bb65-114">`CLR_DEBUGGING_VERSION` Struktura je stejný jako cor_version – struktura, ale je `CLR_DEBUGGING_VERSION` struktura zajišťuje na další struktura pole verze (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="0bb65-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="0bb65-115">V tomto poli musí být v současné době nastavit na nulu.</span><span class="sxs-lookup"><span data-stu-id="0bb65-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bb65-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bb65-116">Requirements</span></span>  
 <span data-ttu-id="0bb65-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bb65-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bb65-118">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="0bb65-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="0bb65-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bb65-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bb65-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bb65-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb65-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bb65-121">See Also</span></span>  
 [<span data-ttu-id="0bb65-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="0bb65-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="0bb65-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="0bb65-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
