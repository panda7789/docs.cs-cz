---
title: "CorTypeAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 501488c0ac03ebf508145572ed73163d7940bfbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
|`tdVisibilityMask`|Používá pro informace o typu viditelnosti.|  
|`tdNotPublic`|Určuje, že typ není v oboru veřejné.|  
|`tdPublic`|Určuje, že typ je v veřejné oboru.|  
|`tdNestedPublic`|Určuje, že je typ vnořené veřejné Přehled.|  
|`tdNestedPrivate`|Určuje, zda je typ vnořené s privátní viditelnost.|  
|`tdNestedFamily`|Určuje, že je typ vnořené rodiny Přehled.|  
|`tdNestedAssembly`|Určuje, zda je typ vnořené s viditelnosti sestavení.|  
|`tdNestedFamANDAssem`|Určuje, že je typ vnořené s viditelnost rodiny a sestavení.|  
|`tdNestedFamORAssem`|Určuje, že je typ vnořené s viditelnost třídu nebo sestavení.|  
|`tdLayoutMask`|Získá informace o typu rozložení.|  
|`tdAutoLayout`|Určuje, že pole tohoto typu jsou nastíněny automaticky.|  
|`tdSequentialLayout`|Určuje, že pole tohoto typu jsou nastíněny postupně.|  
|`tdExplicitLayout`|Určuje, že je explicitně zadat rozložení tohoto pole.|  
|`tdClassSemanticsMask`|Získá sémantické informace o typu.|  
|`tdClass`|Určuje, že je typ třídy.|  
|`tdInterface`|Určuje, že typ je rozhraní.|  
|`tdAbstract`|Určuje, že typ je abstraktní.|  
|`tdSealed`|Určuje, že typ nelze rozšířit.|  
|`tdSpecialName`|Určuje, zda název třídy je speciální. Popisuje, jeho název jak.|  
|`tdImport`|Určuje, zda je typ naimportovány.|  
|`tdSerializable`|Určuje, že typ je serializovatelný.|  
|`tdWindowsRuntime`|Určuje, že je tento typ [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typu.|  
|`tdStringFormatMask`|Získá informace o tom, jak jsou řetězců kódování a formátu.|  
|`tdAnsiClass`|Určuje, že tento typ interpretuje LPTSTR jako ANSI.|  
|`tdUnicodeClass`|Určuje, že tento typ interpretuje LPTSTR jako kódování Unicode.|  
|`tdAutoClass`|Určuje, že tento typ interpretuje LPTSTR automaticky.|  
|`tdCustomFormatClass`|Určuje, že typ má nestandardní kódování, jak je stanoveno `CustomFormatMask`.|  
|`tdCustomFormatMask`|Tato maska slouží k získání nestandardní kódování informací pro nativní zprostředkovatel komunikace s objekty. Význam hodnot těchto dvou BITS není zadáno.|  
|`tdBeforeFieldInit`|Určuje, že typ se musí inicializovat před první pokus o přístup k statické pole.|  
|`tdForwarder`|Určuje, že je typ exportovány a typ předávání.|  
|`tdReservedMask`|Tento příznak a níže uvedené značky se používá interně modul common language runtime.|  
|`tdRTSpecialName`|Určuje, že by měl modul common language runtime kontrolovat kódování názvu.|  
|`tdHasSecurity`|Určuje, zda má tento typ zabezpečení s ním spojená.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
