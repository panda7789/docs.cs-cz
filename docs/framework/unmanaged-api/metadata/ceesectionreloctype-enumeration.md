---
title: CeeSectionRelocType – výčet
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882242da493c49a2e6aa09888e9503dcf2933589
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906136"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="3f7dd-102">CeeSectionRelocType – výčet</span><span class="sxs-lookup"><span data-stu-id="3f7dd-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="3f7dd-103">Poskytuje hodnoty k ovlivnění typu `reloc` instrukci, protože ho ve volání [iceegen::addsectionreloc –](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="3f7dd-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f7dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f7dd-104">Syntax</span></span>  
  
```  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="3f7dd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3f7dd-105">Members</span></span>  
  
|<span data-ttu-id="3f7dd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3f7dd-106">Member</span></span>|<span data-ttu-id="3f7dd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f7dd-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="3f7dd-108">Generuje pouze část – relativní `reloc`Nastěhovat nic do .reloc oddílu.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="3f7dd-109">Generuje `reloc` pro umístění velikosti ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="3f7dd-110">To se transformuje na BASED_HIGHLOW nebo BASED_DIR64 podle platformy.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="3f7dd-111">Generuje `reloc` pro horní 16 bitů 32bitová čísla, kde další slovo v tabulce .reloc součástí dolní 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="3f7dd-112">Generuje token mapy přemístění, odesílání nic do části .reloc.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="3f7dd-113">Označuje, že hodnota je relativní adresa opravy.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="3f7dd-114">Generuje pouze část – relativní `reloc`Nastěhovat nic do .reloc oddílu.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="3f7dd-115">To `reloc` je relativní vzhledem k umístění souboru oddílu, ne v části virtuální adresy.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="3f7dd-116">Určuje kód relativní adresa opravy.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="3f7dd-117">Generuje `reloc` 64bitových adres v ia64 `movl` instrukce.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="3f7dd-118">Generuje `reloc` 64-bit adresy.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="3f7dd-119">Generování `reloc` pro PC relativní adresu 25-bit ia64 `br.call` instrukce.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="3f7dd-120">Generuje `reloc` pro PC relativní adresu 64-bit ia64 `brl.call` instrukce.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="3f7dd-121">Generuje vláknům části 30-bit `reloc`, která se používá pro hodnoty příznakem ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="3f7dd-122">Hodnotu sentinel k zajištění jakékoli dodatky na tento výčet se projeví na vnitřní `reloc` název pole.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="3f7dd-123">Určuje, že generování základní `reloc`.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="3f7dd-124">Hodnota označující, že jsou pre oprava obsah paměti ukazatel, nikoli oddíl posun.</span><span class="sxs-lookup"><span data-stu-id="3f7dd-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f7dd-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f7dd-125">Requirements</span></span>  
 <span data-ttu-id="3f7dd-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f7dd-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f7dd-127">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f7dd-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f7dd-128">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f7dd-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f7dd-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f7dd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7dd-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f7dd-130">See also</span></span>

- [<span data-ttu-id="3f7dd-131">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="3f7dd-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="3f7dd-132">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f7dd-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="3f7dd-133">AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="3f7dd-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
