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
# <a name="cvstruct-structure"></a><span data-ttu-id="064a9-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="064a9-102">CVStruct Structure</span></span>
<span data-ttu-id="064a9-103">Obsahuje informace, které se používají při instalaci modulu nebo složené image.</span><span class="sxs-lookup"><span data-stu-id="064a9-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="064a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="064a9-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="064a9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="064a9-105">Members</span></span>  
  
|<span data-ttu-id="064a9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="064a9-106">Member</span></span>|<span data-ttu-id="064a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="064a9-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="064a9-108">Závažná</span><span class="sxs-lookup"><span data-stu-id="064a9-108">Major</span></span>|<span data-ttu-id="064a9-109">Číslo sestavení hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="064a9-109">Major version build number.</span></span>|  
|<span data-ttu-id="064a9-110">Méně závažná</span><span class="sxs-lookup"><span data-stu-id="064a9-110">Minor</span></span>|<span data-ttu-id="064a9-111">Číslo sestavení dílčí verze</span><span class="sxs-lookup"><span data-stu-id="064a9-111">Minor version build number.</span></span>|  
|<span data-ttu-id="064a9-112">Sub</span><span class="sxs-lookup"><span data-stu-id="064a9-112">Sub</span></span>|<span data-ttu-id="064a9-113">Číslo dílčího sestavení</span><span class="sxs-lookup"><span data-stu-id="064a9-113">Sub-build number.</span></span>|  
|<span data-ttu-id="064a9-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="064a9-114">Build</span></span>|<span data-ttu-id="064a9-115">Číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="064a9-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="064a9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="064a9-116">Requirements</span></span>  
 <span data-ttu-id="064a9-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="064a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="064a9-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="064a9-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="064a9-119">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="064a9-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="064a9-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="064a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064a9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="064a9-121">See also</span></span>

- [<span data-ttu-id="064a9-122">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="064a9-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
