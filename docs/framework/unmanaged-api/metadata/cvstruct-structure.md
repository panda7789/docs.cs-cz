---
title: "CVStruct – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CVStruct
api_location: mscoree.dll
api_type: COM
f1_keywords: CVStruct
helpviewer_keywords: CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95c1aeb0cacef929e99e5121f29e2f69b320caec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="88609-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="88609-102">CVStruct Structure</span></span>
<span data-ttu-id="88609-103">Obsahuje informace, které se používá při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="88609-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88609-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88609-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="88609-105">Členové</span><span class="sxs-lookup"><span data-stu-id="88609-105">Members</span></span>  
  
|<span data-ttu-id="88609-106">Člen</span><span class="sxs-lookup"><span data-stu-id="88609-106">Member</span></span>|<span data-ttu-id="88609-107">Popis</span><span class="sxs-lookup"><span data-stu-id="88609-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="88609-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="88609-108">Major</span></span>|<span data-ttu-id="88609-109">Číslo sestavení hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="88609-109">Major version build number.</span></span>|  
|<span data-ttu-id="88609-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="88609-110">Minor</span></span>|<span data-ttu-id="88609-111">Číslo sestavení podverze.</span><span class="sxs-lookup"><span data-stu-id="88609-111">Minor version build number.</span></span>|  
|<span data-ttu-id="88609-112">Sub</span><span class="sxs-lookup"><span data-stu-id="88609-112">Sub</span></span>|<span data-ttu-id="88609-113">Číslo dílčí sestavení.</span><span class="sxs-lookup"><span data-stu-id="88609-113">Sub-build number.</span></span>|  
|<span data-ttu-id="88609-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="88609-114">Build</span></span>|<span data-ttu-id="88609-115">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="88609-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88609-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88609-116">Requirements</span></span>  
 <span data-ttu-id="88609-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88609-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88609-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="88609-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88609-119">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88609-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88609-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88609-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88609-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="88609-121">See Also</span></span>  
 [<span data-ttu-id="88609-122">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="88609-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
