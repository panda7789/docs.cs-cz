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
ms.openlocfilehash: 2f66d34fcfdd8c61dcc92817ec1a928ac5b603fc
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008895"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="05460-102">ICeeGen::AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="05460-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="05460-103">Přidá instrukci. přemístění do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="05460-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="05460-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="05460-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05460-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05460-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05460-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05460-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="05460-107">pro Část kódu v paměti, do které chcete přidat instrukci. přemístění.</span><span class="sxs-lookup"><span data-stu-id="05460-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="05460-108">pro Posun oddílu</span><span class="sxs-lookup"><span data-stu-id="05460-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="05460-109">pro Oddíl, na který `offset` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="05460-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="05460-110">pro Jedna z hodnot [CeeSectionRelocType –](ceesectionreloctype-enumeration.md) , která určuje druh instrukcí. přemístění, která se má přidat.</span><span class="sxs-lookup"><span data-stu-id="05460-110">[in] One of the [CeeSectionRelocType](ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05460-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05460-111">Requirements</span></span>  
 <span data-ttu-id="05460-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05460-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05460-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="05460-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05460-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="05460-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05460-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05460-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05460-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="05460-116">See also</span></span>

- [<span data-ttu-id="05460-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05460-117">ICeeGen Interface</span></span>](iceegen-interface.md)
