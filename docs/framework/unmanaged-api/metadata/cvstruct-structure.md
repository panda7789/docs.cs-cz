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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905629"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="70598-102">CVStruct – struktura</span><span class="sxs-lookup"><span data-stu-id="70598-102">CVStruct Structure</span></span>
<span data-ttu-id="70598-103">Obsahuje informace, které se použijí při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="70598-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70598-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70598-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="70598-105">Členové</span><span class="sxs-lookup"><span data-stu-id="70598-105">Members</span></span>  
  
|<span data-ttu-id="70598-106">Člen</span><span class="sxs-lookup"><span data-stu-id="70598-106">Member</span></span>|<span data-ttu-id="70598-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70598-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="70598-108">Hlavní</span><span class="sxs-lookup"><span data-stu-id="70598-108">Major</span></span>|<span data-ttu-id="70598-109">Číslo hlavní verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="70598-109">Major version build number.</span></span>|  
|<span data-ttu-id="70598-110">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="70598-110">Minor</span></span>|<span data-ttu-id="70598-111">Číslo podverze sestavení.</span><span class="sxs-lookup"><span data-stu-id="70598-111">Minor version build number.</span></span>|  
|<span data-ttu-id="70598-112">Sub</span><span class="sxs-lookup"><span data-stu-id="70598-112">Sub</span></span>|<span data-ttu-id="70598-113">Dílčí číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="70598-113">Sub-build number.</span></span>|  
|<span data-ttu-id="70598-114">Sestavení</span><span class="sxs-lookup"><span data-stu-id="70598-114">Build</span></span>|<span data-ttu-id="70598-115">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="70598-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70598-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70598-116">Requirements</span></span>  
 <span data-ttu-id="70598-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70598-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70598-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70598-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70598-119">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70598-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70598-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70598-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70598-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70598-121">See also</span></span>

- [<span data-ttu-id="70598-122">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="70598-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
