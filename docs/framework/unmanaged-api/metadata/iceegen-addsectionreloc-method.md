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
ms.openlocfilehash: 7d50f7488c2b231ea66c12cc4903469d9e2337fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088376"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="84fd1-102">ICeeGen::AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="84fd1-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="84fd1-103">Přidá .reloc instrukce k základu kódu.</span><span class="sxs-lookup"><span data-stu-id="84fd1-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="84fd1-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="84fd1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84fd1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84fd1-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84fd1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="84fd1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="84fd1-107">[in] V části kódu v paměti, do které chcete přidat .reloc instrukce.</span><span class="sxs-lookup"><span data-stu-id="84fd1-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="84fd1-108">[in] Posun oddílu.</span><span class="sxs-lookup"><span data-stu-id="84fd1-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="84fd1-109">[in] Oddíl, do které `offset` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="84fd1-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="84fd1-110">[in] Jeden z [ceesectionreloctype –](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) hodnoty určující druh .reloc pokyny, jak přidat.</span><span class="sxs-lookup"><span data-stu-id="84fd1-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84fd1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84fd1-111">Requirements</span></span>  
 <span data-ttu-id="84fd1-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84fd1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84fd1-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="84fd1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84fd1-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84fd1-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84fd1-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84fd1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fd1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84fd1-116">See also</span></span>

- [<span data-ttu-id="84fd1-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84fd1-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
