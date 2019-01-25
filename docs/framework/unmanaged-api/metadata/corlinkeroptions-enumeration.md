---
title: CorLinkerOptions – výčet
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a072e124343641c9f75fb9f924a6409efc8e1d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719934"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="c443c-102">CorLinkerOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="c443c-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="c443c-103">Určuje příznaky a možnosti pro linker metadat.</span><span class="sxs-lookup"><span data-stu-id="c443c-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c443c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c443c-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="c443c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c443c-105">Members</span></span>  
  
|<span data-ttu-id="c443c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c443c-106">Member</span></span>|<span data-ttu-id="c443c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c443c-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="c443c-108">Privátní typy a globální funkce není zachováno.</span><span class="sxs-lookup"><span data-stu-id="c443c-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="c443c-109">Privátní typy a globální funkce jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="c443c-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c443c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c443c-110">Requirements</span></span>  
 <span data-ttu-id="c443c-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c443c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c443c-112">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c443c-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c443c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c443c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c443c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c443c-114">See also</span></span>
- [<span data-ttu-id="c443c-115">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="c443c-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
