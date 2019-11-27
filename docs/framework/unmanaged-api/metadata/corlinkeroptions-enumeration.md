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
ms.openlocfilehash: 086e17185df9caa823b44b51cf027f95d635c48d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450268"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="b7f6a-102">CorLinkerOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="b7f6a-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="b7f6a-103">Určuje příznaky pro výběr možností pro linker metadat.</span><span class="sxs-lookup"><span data-stu-id="b7f6a-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7f6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7f6a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="b7f6a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b7f6a-105">Members</span></span>  
  
|<span data-ttu-id="b7f6a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b7f6a-106">Member</span></span>|<span data-ttu-id="b7f6a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b7f6a-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="b7f6a-108">Soukromé typy a globální funkce nejsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="b7f6a-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="b7f6a-109">Soukromé typy a globální funkce jsou zachovány.</span><span class="sxs-lookup"><span data-stu-id="b7f6a-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7f6a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7f6a-110">Requirements</span></span>  
 <span data-ttu-id="b7f6a-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7f6a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7f6a-112">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="b7f6a-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b7f6a-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7f6a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f6a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7f6a-114">See also</span></span>

- [<span data-ttu-id="b7f6a-115">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b7f6a-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
