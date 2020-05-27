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
ms.openlocfilehash: 84791eba7c95d3278bd4650bd7d660e98fcb79d8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008913"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="b6f67-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="b6f67-102">CVStruct Structure</span></span>
<span data-ttu-id="b6f67-103">Obsahuje informace, které se používají při instalaci modulu nebo složené image.</span><span class="sxs-lookup"><span data-stu-id="b6f67-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6f67-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="b6f67-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b6f67-105">Members</span></span>  
  
|<span data-ttu-id="b6f67-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b6f67-106">Member</span></span>|<span data-ttu-id="b6f67-107">Description</span><span class="sxs-lookup"><span data-stu-id="b6f67-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b6f67-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="b6f67-108">Major</span></span>|<span data-ttu-id="b6f67-109">Číslo sestavení hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="b6f67-109">Major version build number.</span></span>|  
|<span data-ttu-id="b6f67-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="b6f67-110">Minor</span></span>|<span data-ttu-id="b6f67-111">Číslo sestavení dílčí verze</span><span class="sxs-lookup"><span data-stu-id="b6f67-111">Minor version build number.</span></span>|  
|<span data-ttu-id="b6f67-112">Sub</span><span class="sxs-lookup"><span data-stu-id="b6f67-112">Sub</span></span>|<span data-ttu-id="b6f67-113">Číslo dílčího sestavení</span><span class="sxs-lookup"><span data-stu-id="b6f67-113">Sub-build number.</span></span>|  
|<span data-ttu-id="b6f67-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="b6f67-114">Build</span></span>|<span data-ttu-id="b6f67-115">Číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="b6f67-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6f67-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6f67-116">Requirements</span></span>  
 <span data-ttu-id="b6f67-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6f67-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f67-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b6f67-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6f67-119">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b6f67-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6f67-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f67-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f67-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6f67-121">See also</span></span>

- [<span data-ttu-id="b6f67-122">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="b6f67-122">Metadata Structures</span></span>](metadata-structures.md)
