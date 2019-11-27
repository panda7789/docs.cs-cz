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
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450313"
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
  
|Člen|Popis|  
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
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
