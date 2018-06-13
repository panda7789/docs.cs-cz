---
title: ICeeGen::AddSectionReloc – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c281d03c6e3774938cfa6e4b4b3a541738b38489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444340"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="76d1e-102">ICeeGen::AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="76d1e-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="76d1e-103">Přidá instrukce .reloc základu kódu.</span><span class="sxs-lookup"><span data-stu-id="76d1e-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="76d1e-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="76d1e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d1e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76d1e-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76d1e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="76d1e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="76d1e-107">[v] V části kódu v paměti, do které chcete přidat .reloc instrukcí.</span><span class="sxs-lookup"><span data-stu-id="76d1e-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="76d1e-108">[v] Posun oddílu.</span><span class="sxs-lookup"><span data-stu-id="76d1e-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="76d1e-109">[v] V části, ke kterému `offset` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="76d1e-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="76d1e-110">[v] Jeden z [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) hodnoty, označující typ .reloc instrukce pro přidání.</span><span class="sxs-lookup"><span data-stu-id="76d1e-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76d1e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76d1e-111">Requirements</span></span>  
 <span data-ttu-id="76d1e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d1e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d1e-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76d1e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76d1e-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76d1e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76d1e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76d1e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d1e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="76d1e-116">See Also</span></span>  
 [<span data-ttu-id="76d1e-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76d1e-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
