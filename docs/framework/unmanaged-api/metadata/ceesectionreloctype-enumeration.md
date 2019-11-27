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
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444154"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="3fe28-102">CeeSectionRelocType – výčet</span><span class="sxs-lookup"><span data-stu-id="3fe28-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="3fe28-103">Poskytuje hodnoty pro ovlivnění typu `reloc` instrukci, která byla vyvolána voláním metody [ICeeGen:: AddSectionReloc –](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="3fe28-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fe28-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="3fe28-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3fe28-105">Members</span></span>  
  
|<span data-ttu-id="3fe28-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3fe28-106">Member</span></span>|<span data-ttu-id="3fe28-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3fe28-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="3fe28-108">Generuje pouze `reloc`relativní k oddílu, který neodesílá nic do oddílu. přemístění.</span><span class="sxs-lookup"><span data-stu-id="3fe28-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="3fe28-109">Vygeneruje `reloc` pro umístění velikosti ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3fe28-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="3fe28-110">To se transformuje na BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformě.</span><span class="sxs-lookup"><span data-stu-id="3fe28-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="3fe28-111">Vygeneruje `reloc` pro prvních 16 bitů 32ho čísla, kde jsou do následujícího slova v tabulce. přemístění zahrnuty dolní 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="3fe28-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="3fe28-112">Vygeneruje přemístění mapy tokenů a pošle nic do oddílu. přemístění.</span><span class="sxs-lookup"><span data-stu-id="3fe28-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="3fe28-113">Označuje, že hodnota je oprava relativní adresy.</span><span class="sxs-lookup"><span data-stu-id="3fe28-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="3fe28-114">Generuje pouze `reloc`relativní k oddílu, který neodesílá nic do oddílu. přemístění.</span><span class="sxs-lookup"><span data-stu-id="3fe28-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="3fe28-115">Tato `reloc` je relativní vzhledem k umístění souboru oddílu, nikoli k virtuální adrese oddílu.</span><span class="sxs-lookup"><span data-stu-id="3fe28-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="3fe28-116">Určuje opravu adresy relativní ke kódu.</span><span class="sxs-lookup"><span data-stu-id="3fe28-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="3fe28-117">Vygeneruje `reloc` pro bitovou adresu 64 v instrukci ia64 `movl`.</span><span class="sxs-lookup"><span data-stu-id="3fe28-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="3fe28-118">Vygeneruje `reloc` pro 64ovou adresu.</span><span class="sxs-lookup"><span data-stu-id="3fe28-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="3fe28-119">Vygeneruje `reloc` pro 25-bitovou adresu na počítači v instrukci ia64 `br.call`.</span><span class="sxs-lookup"><span data-stu-id="3fe28-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="3fe28-120">Generuje `reloc` v instrukci ia64 `brl.call`, která je 64 pro POČÍTAČovou adresu.</span><span class="sxs-lookup"><span data-stu-id="3fe28-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="3fe28-121">Vygeneruje 64bitovou `reloc`relativní sekce, která se používá pro hodnoty s tagovanými ukazateli.</span><span class="sxs-lookup"><span data-stu-id="3fe28-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="3fe28-122">Hodnota Sentinel, která vám umožní zajistit, aby se všechny dodatky k tomuto výčtu projevily v interním poli názvu `reloc`.</span><span class="sxs-lookup"><span data-stu-id="3fe28-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="3fe28-123">Určuje, že se nemá generovat základní `reloc`.</span><span class="sxs-lookup"><span data-stu-id="3fe28-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="3fe28-124">Hodnota, která označuje, že obsah předběžného opravy paměti je ukazatel, nikoli posun oddílu.</span><span class="sxs-lookup"><span data-stu-id="3fe28-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3fe28-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fe28-125">Requirements</span></span>  
 <span data-ttu-id="3fe28-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fe28-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe28-127">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3fe28-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fe28-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3fe28-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fe28-129">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe28-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe28-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fe28-130">See also</span></span>

- [<span data-ttu-id="3fe28-131">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="3fe28-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="3fe28-132">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fe28-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="3fe28-133">AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="3fe28-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
