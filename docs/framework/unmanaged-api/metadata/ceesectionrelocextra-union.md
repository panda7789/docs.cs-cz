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
ms.openlocfilehash: c2e73caa3c69090bca30c8d4a907ddb619bd0ed4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776333"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="b3ae1-102">CeeSectionRelocExtra – sjednocení</span><span class="sxs-lookup"><span data-stu-id="b3ae1-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="b3ae1-103">Představuje posun adresy používané [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní přemístit oddíl.</span><span class="sxs-lookup"><span data-stu-id="b3ae1-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ae1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3ae1-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="b3ae1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b3ae1-105">Members</span></span>  
  
|<span data-ttu-id="b3ae1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b3ae1-106">Member</span></span>|<span data-ttu-id="b3ae1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ae1-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="b3ae1-108">Úprava horní adresu pro oddíl.</span><span class="sxs-lookup"><span data-stu-id="b3ae1-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3ae1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3ae1-109">Requirements</span></span>  
 <span data-ttu-id="b3ae1-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3ae1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3ae1-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3ae1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3ae1-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3ae1-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3ae1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3ae1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ae1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3ae1-114">See also</span></span>

- [<span data-ttu-id="b3ae1-115">Sjednocení pro metadata</span><span class="sxs-lookup"><span data-stu-id="b3ae1-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
