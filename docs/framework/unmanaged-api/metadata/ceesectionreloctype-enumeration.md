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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType – výčet
Poskytuje hodnoty, které `reloc` ovlivňují typ instrukce vyzařované ve volání [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Generuje pouze relativní `reloc`oddíl , odesílání nic do oddílu .reloc.|  
|`srRelocHighLow`|Generuje `reloc` pro umístění velikosti ukazatele. To je transformováno do BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformě.|  
|`srRelocHighAdj`|Generuje `reloc` pro horních 16 bitů 32bitového čísla, kde dolních 16 bitů je zahrnuto v dalším slově v tabulce .reloc.|  
|`srRelocMapToken`|Generuje přemístění mapy tokenů a nic neodesílá do oddílu .reloc.|  
|`srRelocRelative`|Označuje, že hodnota je relativní adresa oprava.|  
|`srRelocFilePos`|Generuje pouze relativní `reloc`oddíl , odesílání nic do oddílu .reloc. To `reloc` je relativní vzhledem k umístění souboru oddílu, nikoli virtuální adresu oddílu.|  
|`srRelocCodeRelative`|Určuje opravu adresy relativní ke kódu.|  
|`srRelocIA64Imm64`|Generuje `reloc` pro 64bitovou adresu v instrukci ia64. `movl`|  
|`srRelocDir64`|Generuje `reloc` pro 64bitovou adresu.|  
|`srRelocIA64PcRel25`|Vygenerujte `reloc` adresu relativní k 25 bitovým `br.call` počítačům v instrukci ia64.|  
|`srRelocIA64PcRel64`|Generuje `reloc` pro 64bitovou adresu relativní k počítači v `brl.call` instrukci ia64.|  
|`srRelocAbsoluteTagged`|Generuje 30bitový relativní `reloc`řez , který se používá pro hodnoty tagovaného ukazatele.|  
|`srRelocSentinel`|Hodnota sentinel, která pomáhá zajistit, aby se všechny dodatky k tomuto výčtu projevily v poli vnitřního `reloc` názvu.|  
|`srNoBaseReloc`|Určuje, že nemá být `reloc`vyzařována základna .|  
|`srRelocPtr`|Hodnota označující, že obsah před opravy paměti jsou ukazatelem spíše než posunu oddílu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
