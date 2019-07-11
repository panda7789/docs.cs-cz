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
ms.openlocfilehash: 1218ee76a3b7a2f501f87adf1e0bc8133d5329b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781339"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType – výčet
Poskytuje hodnoty k ovlivnění typu `reloc` instrukci, protože ho ve volání [iceegen::addsectionreloc –](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Generuje pouze část – relativní `reloc`Nastěhovat nic do .reloc oddílu.|  
|`srRelocHighLow`|Generuje `reloc` pro umístění velikosti ukazatele. To se transformuje na BASED_HIGHLOW nebo BASED_DIR64 podle platformy.|  
|`srRelocHighAdj`|Generuje `reloc` pro horní 16 bitů 32bitová čísla, kde další slovo v tabulce .reloc součástí dolní 16 bitů.|  
|`srRelocMapToken`|Generuje token mapy přemístění, odesílání nic do části .reloc.|  
|`srRelocRelative`|Označuje, že hodnota je relativní adresa opravy.|  
|`srRelocFilePos`|Generuje pouze část – relativní `reloc`Nastěhovat nic do .reloc oddílu. To `reloc` je relativní vzhledem k umístění souboru oddílu, ne v části virtuální adresy.|  
|`srRelocCodeRelative`|Určuje kód relativní adresa opravy.|  
|`srRelocIA64Imm64`|Generuje `reloc` 64bitových adres v ia64 `movl` instrukce.|  
|`srRelocDir64`|Generuje `reloc` 64-bit adresy.|  
|`srRelocIA64PcRel25`|Generování `reloc` pro PC relativní adresu 25-bit ia64 `br.call` instrukce.|  
|`srRelocIA64PcRel64`|Generuje `reloc` pro PC relativní adresu 64-bit ia64 `brl.call` instrukce.|  
|`srRelocAbsoluteTagged`|Generuje vláknům části 30-bit `reloc`, která se používá pro hodnoty příznakem ukazatele.|  
|`srRelocSentinel`|Hodnotu sentinel k zajištění jakékoli dodatky na tento výčet se projeví na vnitřní `reloc` název pole.|  
|`srNoBaseReloc`|Určuje, že generování základní `reloc`.|  
|`srRelocPtr`|Hodnota označující, že jsou pre oprava obsah paměti ukazatel, nikoli oddíl posun.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
