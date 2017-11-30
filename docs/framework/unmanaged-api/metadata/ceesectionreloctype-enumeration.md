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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType – výčet
Poskytuje hodnoty k ovlivnění typ `reloc` instrukce vygenerované v volání [iceegen::addsectionreloc –](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`srRelocAbsolute`|Generuje pouze část – relativní `reloc`, odesílání nic do části .reloc.|  
|`srRelocHighLow`|Generuje `reloc` pro umístění velikost ukazatele. To je převede na BASED_HIGHLOW nebo BASED_DIR64 v závislosti na platformu.|  
|`srRelocHighAdj`|Generuje `reloc` pro horní 16 bitů 32bitové číslo, kde další aplikace word v tabulce .reloc součástí dolní 16 bitů.|  
|`srRelocMapToken`|Generuje token mapy přemístění, odesílání nic do části .reloc.|  
|`srRelocRelative`|Označuje, že hodnota je relativní adresu opravit.|  
|`srRelocFilePos`|Generuje pouze část – relativní `reloc`, odesílání nic do části .reloc. To `reloc` je relativní vzhledem ke pozice v souboru oddílu, není v části virtuální adresa.|  
|`srRelocCodeRelative`|Určuje kód relativní adresu opravit.|  
|`srRelocIA64Imm64`|Generuje `reloc` pro 64bitové adresu ve ia64 `movl` instrukcí.|  
|`srRelocDir64`|Generuje `reloc` pro adresu 64-bit.|  
|`srRelocIA64PcRel25`|Generování `reloc` pro počítač relativní adresu 25 bitů ve ia64 `br.call` instrukcí.|  
|`srRelocIA64PcRel64`|Generuje `reloc` pro počítač relativní adresu 64-bit ve ia64 `brl.call` instrukcí.|  
|`srRelocAbsoluteTagged`|Generuje 30bitového části – relativní `reloc`používané k hodnot s příznakem ukazatele.|  
|`srRelocSentinel`|Hodnotu sentinel k zajištění všech doplňky tento výčet, se projeví na interní `reloc` název pole.|  
|`srNoBaseReloc`|Určuje, že emitování na základní `reloc`.|  
|`srRelocPtr`|Hodnota označující, že jsou pre oprava obsah paměti ukazatele, nikoli oddíl posun.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [Iceegen – rozhraní](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [Addsectionreloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
