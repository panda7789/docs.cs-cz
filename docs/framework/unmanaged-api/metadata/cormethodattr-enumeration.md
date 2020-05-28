---
title: CorMethodAttr – výčet
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 779a8f88b7521aa4b0a75594552981b41714ee3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007673"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr – výčet
Obsahuje hodnoty, které popisují funkce metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`mdMemberAccessMask`|Určuje přístup ke členu.|  
|`mdPrivateScope`|Určuje, že na člena nelze odkazovat.|  
|`mdPrivate`|Určuje, že člen je přístupný pouze nadřazenému typu.|  
|`mdFamANDAssem`|Určuje, že člen je přístupný podtypy pouze v tomto sestavení.|  
|`mdAssem`|Určuje, že člen je accessibly kýmkoli v sestavení.|  
|`mdFamily`|Určuje, že člen je přístupný pouze pomocí typu a podtypů.|  
|`mdFamORAssem`|Určuje, že člen je přístupný odvozenými třídami a jinými typy v jeho sestavení.|  
|`mdPublic`|Určuje, že je člen přístupný pro všechny typy s přístupem k oboru.|  
|`mdStatic`|Určuje, že je člen definován jako součást typu, nikoli jako člen instance.|  
|`mdFinal`|Určuje, že metodu nelze přepsat.|  
|`mdVirtual`|Určuje, že metoda může být přepsána.|  
|`mdHideBySig`|Určuje, že metoda bude skryta podle názvu a signatury, nikoli jenom podle názvu.|  
|`mdVtableLayoutMask`|Určuje rozložení virtuální tabulky.|  
|`mdReuseSlot`|Určuje, že se má znovu použít slot používaný pro tuto metodu ve virtuální tabulce. Toto nastavení je výchozí.|  
|`mdNewSlot`|Určuje, že metoda vždy získá novou pozici ve virtuální tabulce.|  
|`mdCheckAccessOnOverride`|Určuje, že metodu lze přepsat stejnými typy, pro které jsou viditelné.|  
|`mdAbstract`|Určuje, že metoda není implementována.|  
|`mdSpecialName`|Určuje, že metoda je zvláštní a že její název popisuje, jak.|  
|`mdPinvokeImpl`|Určuje, že implementace metody je předána pomocí PInvoke.|  
|`mdUnmanagedExport`|Určuje, že metoda je spravovaná metoda exportovaná do nespravovaného kódu.|  
|`mdReservedMask`|Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).|  
|`mdRTSpecialName`|Určuje, že modul CLR (Common Language Runtime) by měl kontrolovat kódování názvu metody.|  
|`mdHasSecurity`|Určuje, že k metodě je přidruženo zabezpečení.|  
|`mdRequireSecObject`|Určuje, že metoda volá jinou metodu obsahující bezpečnostní kód.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
