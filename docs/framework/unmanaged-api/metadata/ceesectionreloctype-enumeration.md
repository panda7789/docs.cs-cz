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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176211"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="d3d80-102">CeeSectionRelocType – výčet</span><span class="sxs-lookup"><span data-stu-id="d3d80-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="d3d80-103">Poskytuje hodnoty, které `reloc` ovlivňují typ instrukce vyzařované ve volání [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="d3d80-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3d80-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d3d80-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d3d80-105">Members</span></span>  
  
|<span data-ttu-id="d3d80-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d3d80-106">Member</span></span>|<span data-ttu-id="d3d80-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d3d80-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="d3d80-108">Generuje pouze relativní `reloc`oddíl , odesílání nic do oddílu .reloc.</span><span class="sxs-lookup"><span data-stu-id="d3d80-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="d3d80-109">Generuje `reloc` pro umístění velikosti ukazatele.</span><span class="sxs-lookup"><span data-stu-id="d3d80-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="d3d80-110">To je transformováno do BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformě.</span><span class="sxs-lookup"><span data-stu-id="d3d80-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="d3d80-111">Generuje `reloc` pro horních 16 bitů 32bitového čísla, kde dolních 16 bitů je zahrnuto v dalším slově v tabulce .reloc.</span><span class="sxs-lookup"><span data-stu-id="d3d80-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="d3d80-112">Generuje přemístění mapy tokenů a nic neodesílá do oddílu .reloc.</span><span class="sxs-lookup"><span data-stu-id="d3d80-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="d3d80-113">Označuje, že hodnota je relativní adresa oprava.</span><span class="sxs-lookup"><span data-stu-id="d3d80-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="d3d80-114">Generuje pouze relativní `reloc`oddíl , odesílání nic do oddílu .reloc.</span><span class="sxs-lookup"><span data-stu-id="d3d80-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="d3d80-115">To `reloc` je relativní vzhledem k umístění souboru oddílu, nikoli virtuální adresu oddílu.</span><span class="sxs-lookup"><span data-stu-id="d3d80-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="d3d80-116">Určuje opravu adresy relativní ke kódu.</span><span class="sxs-lookup"><span data-stu-id="d3d80-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="d3d80-117">Generuje `reloc` pro 64bitovou adresu v instrukci ia64. `movl`</span><span class="sxs-lookup"><span data-stu-id="d3d80-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="d3d80-118">Generuje `reloc` pro 64bitovou adresu.</span><span class="sxs-lookup"><span data-stu-id="d3d80-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="d3d80-119">Vygenerujte `reloc` adresu relativní k 25 bitovým `br.call` počítačům v instrukci ia64.</span><span class="sxs-lookup"><span data-stu-id="d3d80-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="d3d80-120">Generuje `reloc` pro 64bitovou adresu relativní k počítači v `brl.call` instrukci ia64.</span><span class="sxs-lookup"><span data-stu-id="d3d80-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="d3d80-121">Generuje 30bitový relativní `reloc`řez , který se používá pro hodnoty tagovaného ukazatele.</span><span class="sxs-lookup"><span data-stu-id="d3d80-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="d3d80-122">Hodnota sentinel, která pomáhá zajistit, aby se všechny dodatky k tomuto výčtu projevily v poli vnitřního `reloc` názvu.</span><span class="sxs-lookup"><span data-stu-id="d3d80-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="d3d80-123">Určuje, že nemá být `reloc`vyzařována základna .</span><span class="sxs-lookup"><span data-stu-id="d3d80-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="d3d80-124">Hodnota označující, že obsah před opravy paměti jsou ukazatelem spíše než posunu oddílu.</span><span class="sxs-lookup"><span data-stu-id="d3d80-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3d80-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3d80-125">Requirements</span></span>  
 <span data-ttu-id="d3d80-126">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d80-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d80-127">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d3d80-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3d80-128">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3d80-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3d80-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d80-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d80-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3d80-130">See also</span></span>

- [<span data-ttu-id="d3d80-131">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="d3d80-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="d3d80-132">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3d80-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="d3d80-133">AddSectionReloc – metoda</span><span class="sxs-lookup"><span data-stu-id="d3d80-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
