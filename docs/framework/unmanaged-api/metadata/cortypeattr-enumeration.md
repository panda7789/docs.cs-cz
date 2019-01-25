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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af90055c0a51e61d4032e45d6fa4a4914ddd045f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667934"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr – výčet
Obsahuje hodnoty, které označují typ metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`tdVisibilityMask`|Používá pro informace o viditelnosti typu.|  
|`tdNotPublic`|Určuje, že typ není v oboru veřejné.|  
|`tdPublic`|Určuje, že typ je ve veřejné oboru.|  
|`tdNestedPublic`|Určuje, že typ je vnořená s veřejnou viditelností.|  
|`tdNestedPrivate`|Určuje, že typ je vnořená s privátní viditelnost.|  
|`tdNestedFamily`|Určuje, že typ je vnořená prostřednictvím řady viditelnosti.|  
|`tdNestedAssembly`|Určuje, že je vnořený typ se viditelností sestavení.|  
|`tdNestedFamANDAssem`|Určuje, že typ je vnořená family a assembly je prozkoumat.|  
|`tdNestedFamORAssem`|Určuje, že typ je vnořená family nebo assembly je prozkoumat.|  
|`tdLayoutMask`|Získá informace o rozložení typu.|  
|`tdAutoLayout`|Určuje, zda jsou automaticky rozloženy pole tohoto typu.|  
|`tdSequentialLayout`|Určuje, že pole tohoto typu jsou rozloženy postupně.|  
|`tdExplicitLayout`|Určuje, že rozložení tohoto pole je explicitně zadán.|  
|`tdClassSemanticsMask`|Získá sémantické informace o typu.|  
|`tdClass`|Určuje, že typ je třída.|  
|`tdInterface`|Určuje, že je typem rozhraní.|  
|`tdAbstract`|Určuje, že typ je abstraktní.|  
|`tdSealed`|Určuje, že typ nelze rozšířit.|  
|`tdSpecialName`|Určuje, že název třídy je speciální. Její název popisuje jak.|  
|`tdImport`|Určuje, že typ je importovat.|  
|`tdSerializable`|Určuje, že typ je serializovatelný.|  
|`tdWindowsRuntime`|Určuje, jestli je tento typ [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.|  
|`tdStringFormatMask`|Získá informace o tom, jak jsou řetězce kódování a ve formátu.|  
|`tdAnsiClass`|Určuje, že tento typ interpretuje LPTSTR jako ANSI.|  
|`tdUnicodeClass`|Určuje, že tento typ interpretuje LPTSTR znakové sady Unicode.|  
|`tdAutoClass`|Určuje, že tento typ interpretuje LPTSTR automaticky.|  
|`tdCustomFormatClass`|Určuje, zda typ má nestandardní kódování, jak je stanoveno `CustomFormatMask`.|  
|`tdCustomFormatMask`|Použijte tuto masku nestandardní kódování informace pro nativní zprostředkovatele komunikace s objekty. Význam hodnot tyto dva bity není zadána.|  
|`tdBeforeFieldInit`|Určuje, že typ musí být inicializován před prvním pokusu o přístup ke statickému poli.|  
|`tdForwarder`|Určuje, že typ je exportovali a předávání typů.|  
|`tdReservedMask`|Tento příznak a příznaky níže se používá interně modulem common language runtime.|  
|`tdRTSpecialName`|Určuje, že modul common language runtime by měla kontrolovat název kódování.|  
|`tdHasSecurity`|Určuje, že má typ zabezpečení, které s ním spojená.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
