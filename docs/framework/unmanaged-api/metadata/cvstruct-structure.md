---
title: CVStruct – struktura
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
ms.openlocfilehash: 19ee3097dfe80ba9dcbdaf316db0fd165b50abc6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436423"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="83503-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="83503-102">CVStruct Structure</span></span>
<span data-ttu-id="83503-103">Contains information that is used when installing a module or a composite image.</span><span class="sxs-lookup"><span data-stu-id="83503-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83503-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83503-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="83503-105">Členové</span><span class="sxs-lookup"><span data-stu-id="83503-105">Members</span></span>  
  
|<span data-ttu-id="83503-106">Člen</span><span class="sxs-lookup"><span data-stu-id="83503-106">Member</span></span>|<span data-ttu-id="83503-107">Popis</span><span class="sxs-lookup"><span data-stu-id="83503-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="83503-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="83503-108">Major</span></span>|<span data-ttu-id="83503-109">Major version build number.</span><span class="sxs-lookup"><span data-stu-id="83503-109">Major version build number.</span></span>|  
|<span data-ttu-id="83503-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="83503-110">Minor</span></span>|<span data-ttu-id="83503-111">Minor version build number.</span><span class="sxs-lookup"><span data-stu-id="83503-111">Minor version build number.</span></span>|  
|<span data-ttu-id="83503-112">Sub</span><span class="sxs-lookup"><span data-stu-id="83503-112">Sub</span></span>|<span data-ttu-id="83503-113">Sub-build number.</span><span class="sxs-lookup"><span data-stu-id="83503-113">Sub-build number.</span></span>|  
|<span data-ttu-id="83503-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="83503-114">Build</span></span>|<span data-ttu-id="83503-115">Build number.</span><span class="sxs-lookup"><span data-stu-id="83503-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83503-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83503-116">Requirements</span></span>  
 <span data-ttu-id="83503-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83503-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83503-118">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83503-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83503-119">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83503-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83503-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83503-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83503-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83503-121">See also</span></span>

- [<span data-ttu-id="83503-122">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="83503-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
