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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3e35cea4601c8e51eb3021dc9f598ddb881afe0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750718"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="cc16d-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="cc16d-102">CVStruct Structure</span></span>
<span data-ttu-id="cc16d-103">Obsahuje informace, které se použijí při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="cc16d-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc16d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc16d-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="cc16d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cc16d-105">Members</span></span>  
  
|<span data-ttu-id="cc16d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cc16d-106">Member</span></span>|<span data-ttu-id="cc16d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cc16d-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cc16d-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="cc16d-108">Major</span></span>|<span data-ttu-id="cc16d-109">Číslo hlavní verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc16d-109">Major version build number.</span></span>|  
|<span data-ttu-id="cc16d-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="cc16d-110">Minor</span></span>|<span data-ttu-id="cc16d-111">Číslo podverze sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc16d-111">Minor version build number.</span></span>|  
|<span data-ttu-id="cc16d-112">Sub</span><span class="sxs-lookup"><span data-stu-id="cc16d-112">Sub</span></span>|<span data-ttu-id="cc16d-113">Dílčí číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc16d-113">Sub-build number.</span></span>|  
|<span data-ttu-id="cc16d-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="cc16d-114">Build</span></span>|<span data-ttu-id="cc16d-115">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc16d-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc16d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc16d-116">Requirements</span></span>  
 <span data-ttu-id="cc16d-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc16d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc16d-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cc16d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc16d-119">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc16d-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc16d-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc16d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc16d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc16d-121">See also</span></span>

- [<span data-ttu-id="cc16d-122">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="cc16d-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
