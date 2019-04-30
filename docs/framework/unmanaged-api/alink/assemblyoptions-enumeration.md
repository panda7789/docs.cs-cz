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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790101"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions – výčet
Vytvoří výčet možností sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|optAssemTitle|String – představuje název sestavení.|  
|optAssemDescription|String – obsahuje popis sestavení.|  
|optAssemConfig|String – obsahuje konfiguraci sestavení.|  
|optAssemOS|String – zakódován jako: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|String – obsahuje národní prostředí sestavení.|  
|optAssemVersion|String – zakódován jako: "Major.Minor.Build.Revision".|  
|optAssemCompany|String – obsahuje společnosti.|  
|optAssemProduct|String – obsahuje název produktu.|  
|optAssemProductVersion|Řetězec (označované také jako InformationalVersion).|  
|optAssemCopyright|String – obsahuje informace o autorských právech.|  
|optAssemTrademark|String – obsahuje informace o ochranných známkách.|  
|optAssemKeyFile|String (název souboru).|  
|optAssemKeyName|String (název klíče).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|BOOL (označované také jako DelaySign).|  
|optAssemFileVersion|String – kódovaný jako "Hlavníverze.podverze.Build.revize" – stejně jako ProductVersion.|  
|optAssemSatelliteVer|String – kódovaný jako "Hlavníverze.podverze.Build.revize".|  
|optLastAssemOption|Čítač Počet prvků.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** alink.h  
  
 **Knihovna**: alink.dll  
  
## <a name="see-also"></a>Viz také:

- [Al.exe (linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
