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
ms.openlocfilehash: 4a5f06b3f79fed5dac5a6f07650e4fabd0aa5867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142165"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="73343-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="73343-102">CVStruct Structure</span></span>
<span data-ttu-id="73343-103">Obsahuje informace, které se použijí při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="73343-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73343-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="73343-105">Členové</span><span class="sxs-lookup"><span data-stu-id="73343-105">Members</span></span>  
  
|<span data-ttu-id="73343-106">Člen</span><span class="sxs-lookup"><span data-stu-id="73343-106">Member</span></span>|<span data-ttu-id="73343-107">Popis</span><span class="sxs-lookup"><span data-stu-id="73343-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="73343-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="73343-108">Major</span></span>|<span data-ttu-id="73343-109">Číslo hlavní verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="73343-109">Major version build number.</span></span>|  
|<span data-ttu-id="73343-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="73343-110">Minor</span></span>|<span data-ttu-id="73343-111">Číslo podverze sestavení.</span><span class="sxs-lookup"><span data-stu-id="73343-111">Minor version build number.</span></span>|  
|<span data-ttu-id="73343-112">Sub</span><span class="sxs-lookup"><span data-stu-id="73343-112">Sub</span></span>|<span data-ttu-id="73343-113">Dílčí číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="73343-113">Sub-build number.</span></span>|  
|<span data-ttu-id="73343-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="73343-114">Build</span></span>|<span data-ttu-id="73343-115">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="73343-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73343-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73343-116">Requirements</span></span>  
 <span data-ttu-id="73343-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73343-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73343-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="73343-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73343-119">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73343-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="73343-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="73343-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73343-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73343-121">See also</span></span>

- [<span data-ttu-id="73343-122">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="73343-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
