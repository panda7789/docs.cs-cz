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
ms.openlocfilehash: d11fefe220fdb00457cc48a6cd166673350be049
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006026"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="d489f-102">CeeSectionRelocExtra – sjednocení</span><span class="sxs-lookup"><span data-stu-id="d489f-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="d489f-103">Představuje posun adresy, který je používán rozhraním [ICeeGen](iceegen-interface.md) k přemístění oddílu.</span><span class="sxs-lookup"><span data-stu-id="d489f-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d489f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d489f-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="d489f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d489f-105">Members</span></span>  
  
|<span data-ttu-id="d489f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d489f-106">Member</span></span>|<span data-ttu-id="d489f-107">Description</span><span class="sxs-lookup"><span data-stu-id="d489f-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="d489f-108">Horní úprava adresy pro oddíl.</span><span class="sxs-lookup"><span data-stu-id="d489f-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d489f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d489f-109">Requirements</span></span>  
 <span data-ttu-id="d489f-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d489f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d489f-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d489f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d489f-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d489f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d489f-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d489f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d489f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d489f-114">See also</span></span>

- [<span data-ttu-id="d489f-115">Sjednocení pro metadata</span><span class="sxs-lookup"><span data-stu-id="d489f-115">Metadata Unions</span></span>](metadata-unions.md)
