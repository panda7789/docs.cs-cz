---
title: CoreClrDebugRuntimeInfo – struktura
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
ms.openlocfilehash: 2c41e7db32ee8557a6c03217b95fd5b040655c70
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860938"
---
# <a name="coreclrdebugruntimeinfo-structure"></a>CoreClrDebugRuntimeInfo – struktura
Představuje instanci modulu CLR (Common Language Runtime), která je načtena v procesu ve vzdáleném počítači.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`m_dwInternalID`|Identifikátor modulu runtime, který je přiřazený proxy vzdáleného ladění, který běží na cílovém počítači.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Knihovna:** mscordbi_macx86. dll  
  
 **Verze .NET Framework:** 3,5 SP1
