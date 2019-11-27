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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType – výčet
Poskytuje hodnoty pro ovlivnění typu `reloc` instrukci, která byla vyvolána voláním metody [ICeeGen:: AddSectionReloc –](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`srRelocAbsolute`|Generuje pouze `reloc`relativní k oddílu, který neodesílá nic do oddílu. přemístění.|  
|`srRelocHighLow`|Vygeneruje `reloc` pro umístění velikosti ukazatele. To se transformuje na BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformě.|  
|`srRelocHighAdj`|Vygeneruje `reloc` pro prvních 16 bitů 32ho čísla, kde jsou do následujícího slova v tabulce. přemístění zahrnuty dolní 16 bitů.|  
|`srRelocMapToken`|Vygeneruje přemístění mapy tokenů a pošle nic do oddílu. přemístění.|  
|`srRelocRelative`|Označuje, že hodnota je oprava relativní adresy.|  
|`srRelocFilePos`|Generuje pouze `reloc`relativní k oddílu, který neodesílá nic do oddílu. přemístění. Tato `reloc` je relativní vzhledem k umístění souboru oddílu, nikoli k virtuální adrese oddílu.|  
|`srRelocCodeRelative`|Určuje opravu adresy relativní ke kódu.|  
|`srRelocIA64Imm64`|Vygeneruje `reloc` pro bitovou adresu 64 v instrukci ia64 `movl`.|  
|`srRelocDir64`|Vygeneruje `reloc` pro 64ovou adresu.|  
|`srRelocIA64PcRel25`|Vygeneruje `reloc` pro 25-bitovou adresu na počítači v instrukci ia64 `br.call`.|  
|`srRelocIA64PcRel64`|Generuje `reloc` v instrukci ia64 `brl.call`, která je 64 pro POČÍTAČovou adresu.|  
|`srRelocAbsoluteTagged`|Vygeneruje 64bitovou `reloc`relativní sekce, která se používá pro hodnoty s tagovanými ukazateli.|  
|`srRelocSentinel`|Hodnota Sentinel, která vám umožní zajistit, aby se všechny dodatky k tomuto výčtu projevily v interním poli názvu `reloc`.|  
|`srNoBaseReloc`|Určuje, že se nemá generovat základní `reloc`.|  
|`srRelocPtr`|Hodnota, která označuje, že obsah předběžného opravy paměti je ukazatel, nikoli posun oddílu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
