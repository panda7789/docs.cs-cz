---
title: CeeSectionRelocExtra – sjednocení
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a78a4b82d0b2064c90c938a8614b0c7594f7856
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182270"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="56f15-102">CeeSectionRelocExtra – sjednocení</span><span class="sxs-lookup"><span data-stu-id="56f15-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="56f15-103">Představuje posun adresy používané [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní přemístit oddíl.</span><span class="sxs-lookup"><span data-stu-id="56f15-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f15-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="56f15-105">Členové</span><span class="sxs-lookup"><span data-stu-id="56f15-105">Members</span></span>  
  
|<span data-ttu-id="56f15-106">Člen</span><span class="sxs-lookup"><span data-stu-id="56f15-106">Member</span></span>|<span data-ttu-id="56f15-107">Popis</span><span class="sxs-lookup"><span data-stu-id="56f15-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="56f15-108">Úprava horní adresu pro oddíl.</span><span class="sxs-lookup"><span data-stu-id="56f15-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56f15-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f15-109">Requirements</span></span>  
 <span data-ttu-id="56f15-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f15-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56f15-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56f15-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56f15-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="56f15-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56f15-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56f15-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56f15-114">See also</span></span>

- [<span data-ttu-id="56f15-115">Spojení metadat</span><span class="sxs-lookup"><span data-stu-id="56f15-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
