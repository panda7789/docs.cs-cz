---
title: CorTypeAttr – výčet
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b1586184c91619994ba0dfc9d5dcc277c10f99cf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436447"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr – výčet
Obsahuje hodnoty, které označují metadata typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`tdVisibilityMask`|Používá se pro informace o viditelnosti typů.|  
|`tdNotPublic`|Určuje, že tento typ není ve veřejném oboru.|  
|`tdPublic`|Určuje, že typ je ve veřejném oboru.|  
|`tdNestedPublic`|Určuje, že typ je vnořený s veřejnou viditelností.|  
|`tdNestedPrivate`|Určuje, že typ je vnořený s privátní viditelností.|  
|`tdNestedFamily`|Určuje, že typ je vnořen s viditelností rodiny.|  
|`tdNestedAssembly`|Určuje, že typ je vnořen s viditelností sestavení.|  
|`tdNestedFamANDAssem`|Určuje, že typ je vnořen s viditelností rodiny a sestavování sestavení.|  
|`tdNestedFamORAssem`|Určuje, že typ je vnořen s viditelností rodin nebo sestavení.|  
|`tdLayoutMask`|Získá informace o rozložení pro daný typ.|  
|`tdAutoLayout`|Určuje, že pole tohoto typu jsou automaticky rozložena.|  
|`tdSequentialLayout`|Určuje, že pole tohoto typu jsou rozložena sekvenčně.|  
|`tdExplicitLayout`|Určuje, že rozložení pole je zadáno explicitně.|  
|`tdClassSemanticsMask`|Získá sémantické informace o typu.|  
|`tdClass`|Určuje, že typ je třída.|  
|`tdInterface`|Určuje, že typ je rozhraní.|  
|`tdAbstract`|Určuje, že typ je abstraktní.|  
|`tdSealed`|Určuje, že typ nelze rozšířit.|  
|`tdSpecialName`|Určuje, že název třídy je speciální. Jeho název popisuje, jak.|  
|`tdImport`|Určuje, že se typ importuje.|  
|`tdSerializable`|Určuje, že typ je serializovatelný.|  
|`tdWindowsRuntime`|Určuje, že tento typ je prostředí Windows Runtime typ.|  
|`tdStringFormatMask`|Načte informace o tom, jak jsou řetězce kódované a naformátované.|  
|`tdAnsiClass`|Určuje, že tento typ interpretuje LPTSTR jako ANSI.|  
|`tdUnicodeClass`|Určuje, že tento typ interpretuje LPTSTR jako Unicode.|  
|`tdAutoClass`|Určuje, že tento typ interpretuje LPTSTR automaticky.|  
|`tdCustomFormatClass`|Určuje, že typ má nestandardní kódování, jak je určeno `CustomFormatMask`.|  
|`tdCustomFormatMask`|Tuto masku použijte k získání nestandardních informací o kódování pro nativní spolupráci. Význam hodnot těchto dvou bitů není určen.|  
|`tdBeforeFieldInit`|Určuje, že typ musí být inicializován před prvním pokusem o přístup k statickému poli.|  
|`tdForwarder`|Určuje, že je typ exportován, a předávání typu.|  
|`tdReservedMask`|Tento příznak a níže uvedené příznaky se používají interně modulem CLR (Common Language Runtime).|  
|`tdRTSpecialName`|Určuje, že by měl modul CLR (Common Language Runtime) kontrolovat kódování názvu.|  
|`tdHasSecurity`|Určuje, že k typu je přidruženo zabezpečení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
