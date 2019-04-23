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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176992"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr – výčet
Obsahuje hodnoty, které popisují funkce metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
|Člen|Popis|  
|------------|-----------------|  
|`mdMemberAccessMask`|Určuje přístup ke členu.|  
|`mdPrivateScope`|Určuje, že člen se nedá odkazovat.|  
|`mdPrivate`|Určuje, že člen je přístupný pouze pomocí nadřazeného typu.|  
|`mdFamANDAssem`|Určuje, že člen je přístupný pro podtypy pouze v tomto sestavení.|  
|`mdAssem`|Určuje, zda člen accessibly kdokoli v sestavení.|  
|`mdFamily`|Určuje, že člen je přístupný pouze podle typu a podtypy.|  
|`mdFamORAssem`|Určuje, že člen je přístupný z odvozených tříd a další typy v sestavení.|  
|`mdPublic`|Určuje, že člen je přístupné pro všechny typy s přístupem k oboru.|  
|`mdStatic`|Určuje, že člen je definovaný v rámci typu, nikoli jako člena instance.|  
|`mdFinal`|Určuje, že metoda nemůže být přepsána.|  
|`mdVirtual`|Určuje, zda lze přepsat metodu.|  
|`mdHideBySig`|Určuje, že metoda skrývá podle názvu a podpisu, nikoli pouze podle názvu.|  
|`mdVtableLayoutMask`|Určuje rozložení virtuální tabulky.|  
|`mdReuseSlot`|Určuje, že slotu použít pro tuto metodu v tabulce virtuální znovu použít. Toto nastavení je výchozí.|  
|`mdNewSlot`|Určuje, že metoda vždy získá nový slot v tabulce virtuální.|  
|`mdCheckAccessOnOverride`|Určuje, že metoda se dá přepsat stejné typy, na které je viditelné.|  
|`mdAbstract`|Určuje, že metoda není implementována.|  
|`mdSpecialName`|Určuje, že metoda je speciální a že jeho název popisuje jak.|  
|`mdPinvokeImpl`|Určuje, že implementace metody je dál pomocí služby PInvoke.|  
|`mdUnmanagedExport`|Určuje, že metoda je spravované metody exportovat do nespravovaného kódu.|  
|`mdReservedMask`|Modul common language runtime vyhrazené pro interní použití.|  
|`mdRTSpecialName`|Určuje, že modul common language runtime by měla kontrolovat kódování název metody.|  
|`mdHasSecurity`|Určuje, že tato metoda má přidruženo zabezpečení.|  
|`mdRequireSecObject`|Určuje, že metoda volá jinou metodu obsahující zabezpečovací kód.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
