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
ms.openlocfilehash: 195f311d58f2169d715bb33986ee6e591622f377
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445040"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="ac7fb-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="ac7fb-102">CVStruct Structure</span></span>
<span data-ttu-id="ac7fb-103">Obsahuje informace, které se používá při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ac7fb-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac7fb-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="ac7fb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ac7fb-105">Members</span></span>  
  
|<span data-ttu-id="ac7fb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ac7fb-106">Member</span></span>|<span data-ttu-id="ac7fb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ac7fb-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ac7fb-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="ac7fb-108">Major</span></span>|<span data-ttu-id="ac7fb-109">Číslo sestavení hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="ac7fb-109">Major version build number.</span></span>|  
|<span data-ttu-id="ac7fb-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="ac7fb-110">Minor</span></span>|<span data-ttu-id="ac7fb-111">Číslo sestavení podverze.</span><span class="sxs-lookup"><span data-stu-id="ac7fb-111">Minor version build number.</span></span>|  
|<span data-ttu-id="ac7fb-112">Sub</span><span class="sxs-lookup"><span data-stu-id="ac7fb-112">Sub</span></span>|<span data-ttu-id="ac7fb-113">Číslo dílčí sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac7fb-113">Sub-build number.</span></span>|  
|<span data-ttu-id="ac7fb-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="ac7fb-114">Build</span></span>|<span data-ttu-id="ac7fb-115">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac7fb-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac7fb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac7fb-116">Requirements</span></span>  
 <span data-ttu-id="ac7fb-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac7fb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac7fb-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac7fb-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac7fb-119">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac7fb-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac7fb-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac7fb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7fb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac7fb-121">See Also</span></span>  
 [<span data-ttu-id="ac7fb-122">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="ac7fb-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
