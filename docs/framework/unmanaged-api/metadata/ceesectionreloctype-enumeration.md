---
title: "CeeSectionRelocType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionRelocType
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionRelocType
helpviewer_keywords: CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d78b6b3867cb168e4ebf93c07f17a911e1955832
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="5e1d4-102">CeeSectionRelocType – výčet</span><span class="sxs-lookup"><span data-stu-id="5e1d4-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="5e1d4-103">Poskytuje hodnoty k ovlivnění typ `reloc` instrukce vygenerované v volání [iceegen::addsectionreloc –](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="5e1d4-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e1d4-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5e1d4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5e1d4-105">Members</span></span>  
  
|<span data-ttu-id="5e1d4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5e1d4-106">Member</span></span>|<span data-ttu-id="5e1d4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5e1d4-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="5e1d4-108">Generuje pouze část – relativní `reloc`, odesílání nic do části .reloc.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="5e1d4-109">Generuje `reloc` pro umístění velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="5e1d4-110">To je převede na BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformu.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="5e1d4-111">Generuje `reloc` pro horní 16 bitů 32bitové číslo, kde další aplikace word v tabulce .reloc součástí dolní 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="5e1d4-112">Generuje token mapy přemístění, odesílání nic do části .reloc.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="5e1d4-113">Označuje, že hodnota je relativní adresu opravit.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="5e1d4-114">Generuje pouze část – relativní `reloc`, odesílání nic do části .reloc.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="5e1d4-115">To `reloc` je relativní vzhledem ke pozice v souboru oddílu, není v části virtuální adresa.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="5e1d4-116">Určuje kód relativní adresu opravit.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="5e1d4-117">Generuje `reloc` pro 64bitové adresu ve ia64 `movl` instrukcí.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="5e1d4-118">Generuje `reloc` pro adresu 64-bit.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="5e1d4-119">Generování `reloc` pro počítač relativní adresu 25 bitů ve ia64 `br.call` instrukcí.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="5e1d4-120">Generuje `reloc` pro počítač relativní adresu 64-bit ve ia64 `brl.call` instrukcí.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="5e1d4-121">Generuje 30bitového části – relativní `reloc`používané k hodnot s příznakem ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="5e1d4-122">Hodnotu sentinel k zajištění všech doplňky tento výčet, se projeví na interní `reloc` název pole.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="5e1d4-123">Určuje, že emitování na základní `reloc`.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="5e1d4-124">Hodnota označující, že jsou pre oprava obsah paměti ukazatele, nikoli oddíl posun.</span><span class="sxs-lookup"><span data-stu-id="5e1d4-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e1d4-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e1d4-125">Requirements</span></span>  
 <span data-ttu-id="5e1d4-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e1d4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1d4-127">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e1d4-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e1d4-128">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e1d4-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e1d4-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1d4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1d4-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e1d4-130">See Also</span></span>  
 [<span data-ttu-id="5e1d4-131">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="5e1d4-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="5e1d4-132">Iceegen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e1d4-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [<span data-ttu-id="5e1d4-133">Addsectionreloc – metoda</span><span class="sxs-lookup"><span data-stu-id="5e1d4-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
