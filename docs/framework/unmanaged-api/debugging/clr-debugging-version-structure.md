---
title: CLR_DEBUGGING_VERSION – struktura
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 651b916a0e3ca178432094428611f9bcc8f0fd17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132422"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION – struktura
Definuje verzi produktu modulu CLR (Common Language Runtime) pro účely ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`wStructVersion`|Číslo verze struktury|  
|`wMajor`|Hlavní číslo verze.|  
|`wMinor`|Vedlejší číslo verze.|  
|`wBuild`|Číslo sestavení|  
|`wRevision`|Číslo revize|  
  
## <a name="remarks"></a>Poznámky  
 Struktura `CLR_DEBUGGING_VERSION` je stejná jako struktura COR_VERSION, ale struktura `CLR_DEBUGGING_VERSION` poskytuje další pole verze struktury (`wStructVersion`). V současné době musí být toto pole nastaveno na hodnotu nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
