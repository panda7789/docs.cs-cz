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
ms.openlocfilehash: c7634ec801a30aa7ba07954c1df0c3d37ec279eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440298"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="53a0a-102">CeeSectionRelocExtra – sjednocení</span><span class="sxs-lookup"><span data-stu-id="53a0a-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="53a0a-103">Představuje posunem adres, který je používán [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní přesunovat oddíl.</span><span class="sxs-lookup"><span data-stu-id="53a0a-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53a0a-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="53a0a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="53a0a-105">Members</span></span>  
  
|<span data-ttu-id="53a0a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="53a0a-106">Member</span></span>|<span data-ttu-id="53a0a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="53a0a-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="53a0a-108">Úprava horní adresa pro oddíl.</span><span class="sxs-lookup"><span data-stu-id="53a0a-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53a0a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53a0a-109">Requirements</span></span>  
 <span data-ttu-id="53a0a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53a0a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53a0a-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53a0a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53a0a-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53a0a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53a0a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53a0a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a0a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="53a0a-114">See Also</span></span>  
 [<span data-ttu-id="53a0a-115">Sjednocení pro metadata</span><span class="sxs-lookup"><span data-stu-id="53a0a-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
