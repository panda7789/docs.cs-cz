---
title: AssemblyOptions – výčet
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: ed45e06297b77ea60304cdcfe1b08e97f9e4c085
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446587"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions – výčet
Vytvoří výčet možností sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>Pole  
  
|Pole|Popis|  
|-----------|-----------------|  
|optAssemTitle|Řetězec – představuje název sestavení.|  
|optAssemDescription|Řetězec – obsahuje popis sestavení.|  
|optAssemConfig|Řetězec – obsahuje konfiguraci sestavení.|  
|optAssemOS|Řetězec kódovaný jako: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Řetězec – obsahuje národní prostředí sestavení.|  
|optAssemVersion|Řetězec – kódovaný jako: "hlavní_verze. podverze. sestavení. revize".|  
|optAssemCompany|Řetězec – obsahuje společnost.|  
|optAssemProduct|Řetězec – obsahuje název produktu.|  
|optAssemProductVersion|String (označuje se také jako InformationalVersion).|  
|optAssemCopyright|Řetězec – obsahuje informace o autorských právech.|  
|optAssemTrademark|Řetězec – obsahuje informace o ochranných známkách.|  
|optAssemKeyFile|String (název souboru).|  
|optAssemKeyName|Řetězec (název klíče).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (označuje se také jako DelaySign).|  
|optAssemFileVersion|Řetězec – zakódovaný jako "hlavní_verze. podverze. sestavení. revize" – stejné jako ProductVersion.|  
|optAssemSatelliteVer|Řetězec – zakódovaný jako "hlavní_verze. podverze. sestavení. revize".|  
|optLastAssemOption|Čítač počtu prvků.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ALink. h  
  
 **Knihovna**: ALink. dll  
  
## <a name="see-also"></a>Viz také:

- [Al.exe (linker sestavení)](../../tools/al-exe-assembly-linker.md)
