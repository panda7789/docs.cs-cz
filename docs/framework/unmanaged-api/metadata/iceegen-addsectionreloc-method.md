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
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176107"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="7230e-102">ICeeGen::AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="7230e-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="7230e-103">Přidá .reloc instrukce základu kódu.</span><span class="sxs-lookup"><span data-stu-id="7230e-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="7230e-104">Tato metoda je zastaralá a neměla by být použita.</span><span class="sxs-lookup"><span data-stu-id="7230e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7230e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7230e-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7230e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7230e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7230e-107">[v] Část kódu v paměti, do kterého chcete přidat instrukce .reloc.</span><span class="sxs-lookup"><span data-stu-id="7230e-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="7230e-108">[v] Posun oddílu.</span><span class="sxs-lookup"><span data-stu-id="7230e-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="7230e-109">[v] Část, na `offset` kterou se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="7230e-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="7230e-110">[v] Jeden z [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) hodnoty označující druh .reloc instrukce přidat.</span><span class="sxs-lookup"><span data-stu-id="7230e-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7230e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7230e-111">Requirements</span></span>  
 <span data-ttu-id="7230e-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7230e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7230e-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="7230e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7230e-114">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7230e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7230e-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7230e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7230e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7230e-116">See also</span></span>

- [<span data-ttu-id="7230e-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7230e-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
