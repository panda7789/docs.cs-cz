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
ms.openlocfilehash: 78b30f624bd71234e8f1b56600b3a23d15fdf517
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006025"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType – výčet
Poskytuje hodnoty pro ovlivnění typu `reloc` instrukce, která byla vyvolána voláním metody [ICeeGen:: AddSectionReloc –](iceegen-addsectionreloc-method.md).  
  
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
  
|Člen|Description|  
|------------|-----------------|  
|`srRelocAbsolute`|Generuje jenom relativní oddíl, který `reloc` neposílá do oddílu. přemístění žádnou hodnotu.|  
|`srRelocHighLow`|Vygeneruje `reloc` pro umístění velikosti ukazatele. To se transformuje na BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformě.|  
|`srRelocHighAdj`|Vygeneruje hodnotu `reloc` pro prvních 16 bitů 32ho čísla, kde jsou do následujícího slova v tabulce. přemístění zahrnuty dolní 16 bitů.|  
|`srRelocMapToken`|Vygeneruje přemístění mapy tokenů a pošle nic do oddílu. přemístění.|  
|`srRelocRelative`|Označuje, že hodnota je oprava relativní adresy.|  
|`srRelocFilePos`|Generuje jenom relativní oddíl, který `reloc` neposílá do oddílu. přemístění žádnou hodnotu. To `reloc` je relativní vzhledem k umístění souboru oddílu, nikoli k virtuální adrese oddílu.|  
|`srRelocCodeRelative`|Určuje opravu adresy relativní ke kódu.|  
|`srRelocIA64Imm64`|Vygeneruje `reloc` v instrukci ia64 pro 64 bitovou adresu `movl` .|  
|`srRelocDir64`|Vygeneruje `reloc` bitovou adresu pro 64.|  
|`srRelocIA64PcRel25`|Vygenerujte `reloc` v instrukci ia64 pro 25-bitovou adresu v počítači `br.call` .|  
|`srRelocIA64PcRel64`|Vygeneruje `reloc` v instrukci ia64 pro 64ou adresu v počítači `brl.call` .|  
|`srRelocAbsoluteTagged`|Generuje 32bitový oddíl `reloc` , který se používá pro hodnoty s tagovanými ukazateli.|  
|`srRelocSentinel`|Hodnota Sentinel, která vám umožní zajistit, aby se všechny dodatky k tomuto výčtu projevily v poli interní `reloc` název.|  
|`srNoBaseReloc`|Určuje, že se nemá generovat základ `reloc` .|  
|`srRelocPtr`|Hodnota, která označuje, že obsah předběžného opravy paměti je ukazatel, nikoli posun oddílu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
- [ICeeGen – rozhraní](iceegen-interface.md)
- [AddSectionReloc – metoda](iceegen-addsectionreloc-method.md)
