---
title: "AssemblyOptions – výčet"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ad4f9e02ed0d22009fcb8a5ac078231f2cb22e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
|optAssemOS|String – kódovaná jako: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG –|  
|optAssemLocale|String – obsahuje národnímu sestavení.|  
|optAssemVersion|String – kódovaná jako: "Major.Minor.Build.Revision".|  
|optAssemCompany|String – obsahuje společnosti.|  
|optAssemProduct|String – obsahuje název produktu.|  
|optAssemProductVersion|Řetězec (také označované jako InformationalVersion).|  
|optAssemCopyright|String – obsahuje informace o autorských právech.|  
|optAssemTrademark|String – obsahuje informace o ochranných známkách.|  
|optAssemKeyFile|String (název souboru).|  
|optAssemKeyName|String (název klíče).|  
|optAssemAlgID|ULONG –|  
|optAssemFlags|ULONG –|  
|optAssemHalfSign|BOOL (také označované jako DelaySign).|  
|optAssemFileVersion|String – kódovaná jako "Major.Minor.Build.Revision"--stejný jako ProductVersion.|  
|optAssemSatelliteVer|String – kódovaná jako "Major.Minor.Build.Revision".|  
|optLastAssemOption|Čítač Počet elementů.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** alink.h  
  
 **Knihovna**: alink.dll  
  
## <a name="see-also"></a>Viz také  
 [Al.exe (linker sestavení)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
