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
ms.openlocfilehash: e12882e53d1aa2120ab5c4b6793d7f2e34be76eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132167"
---
# <a name="coreclrdebugprocinfo-structure"></a>CoreClrDebugProcInfo – struktura
Představuje proces, který je spuštěn ve vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`m_dwPID`|Identifikátor procesu přiřazený operačním systémem.|  
|`m_dwInternalID`|Identifikátor procesu, který je přiřazený proxy vzdáleného ladění, který běží na cílovém počítači. Tento identifikátor recykluje méně často než identifikátor operačního systému.|  
|`m_wszName`|Příkazový řádek procesu. Tento člen může být zkrácen.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1
