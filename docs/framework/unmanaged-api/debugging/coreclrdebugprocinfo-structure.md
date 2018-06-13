---
title: CoreClrDebugProcInfo – struktura
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9d4b27ca0bf454b42f15b849008e5a3019bb09a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402188"
---
# <a name="coreclrdebugprocinfo-structure"></a>CoreClrDebugProcInfo – struktura
Představuje proces, který běží na vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`m_dwPID`|Identifikátor procesu přiřazené operačního systému.|  
|`m_dwInternalID`|Identifikátor procesu, který je přiřazen nástrojem proxy vzdáleného ladění na cílovém počítači spuštěna. Tento identifikátor recyklování méně často než identifikátor operačního systému.|  
|`m_wszName`|Příkazového řádku procesu. Tento člen mohou být zkráceny.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1
