---
title: CorFieldAttr – výčet
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: dea69e18fc517eddddc5b99950a6f3b16ee3e426
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007400"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr – výčet
Obsahuje hodnoty, které popisují metadata k poli.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`fdFieldAccessMask`|Určuje informace o usnadnění.|  
|`fdPrivateScope`|Určuje, že na pole se nedá odkazovat.|  
|`fdPrivate`|Určuje, že pole je přístupné pouze pomocí jeho nadřazeného typu.|  
|`fdFamANDAssem`|Určuje, že pole je přístupné odvozenými třídami v jeho sestavení.|  
|`fdAssembly`|Určuje, že pole je přístupné pro všechny typy v jeho sestavení.|  
|`fdFamily`|Určuje, že pole je přístupné pouze pomocí jeho typu a odvozených tříd.|  
|`fdFamORAssem`|Určuje, že pole je přístupné odvozenými třídami a všemi typy v jeho sestavení.|  
|`fdPublic`|Určuje, že pole je přístupné pro všechny typy s viditelností tohoto oboru.|  
|`fdStatic`|Určuje, že pole je členem jeho typu, nikoli členem instance.|  
|`fdInitOnly`|Určuje, že pole nelze po inicializaci změnit.|  
|`fdLiteral`|Určuje, že hodnota pole je konstanta při kompilaci.|  
|`fdNotSerialized`|Určuje, že pole není serializováno, pokud je jeho typ vzdáleně vytvořen.|  
|`fdSpecialName`|Určuje, že pole je zvláštní a že jeho název popisuje, jak.|  
|`fdPinvokeImpl`|Určuje, že implementace pole je předána pomocí PInvoke.|  
|`fdReservedMask`|Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).|  
|`fdRTSpecialName`|Určuje, že vnitřní rozhraní API pro Common Language Runtime metadata by měla kontrolovat kódování názvu.|  
|`fdHasFieldMarshal`|Určuje, že pole obsahuje informace o zařazování.|  
|`fdHasDefault`|Určuje, že pole má výchozí hodnotu.|  
|`fdHasFieldRVA`|Určuje, že pole má relativní virtuální adresu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
