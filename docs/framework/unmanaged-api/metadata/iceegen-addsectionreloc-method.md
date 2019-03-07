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
ms.openlocfilehash: 5e74d625cadb2febe45aa4c000e5b63f96aada55
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494100"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="000b5-102">ICeeGen::AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="000b5-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="000b5-103">Přidá .reloc instrukce k základu kódu.</span><span class="sxs-lookup"><span data-stu-id="000b5-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="000b5-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="000b5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="000b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="000b5-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="000b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="000b5-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="000b5-107">[in] V části kódu v paměti, do které chcete přidat .reloc instrukce.</span><span class="sxs-lookup"><span data-stu-id="000b5-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="000b5-108">[in] Posun oddílu.</span><span class="sxs-lookup"><span data-stu-id="000b5-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="000b5-109">[in] Oddíl, do které `offset` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="000b5-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="000b5-110">[in] Jeden z [ceesectionreloctype –](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) hodnoty určující druh .reloc pokyny, jak přidat.</span><span class="sxs-lookup"><span data-stu-id="000b5-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="000b5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="000b5-111">Requirements</span></span>  
 <span data-ttu-id="000b5-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="000b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="000b5-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="000b5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="000b5-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="000b5-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="000b5-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="000b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="000b5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="000b5-116">See also</span></span>
- [<span data-ttu-id="000b5-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="000b5-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
