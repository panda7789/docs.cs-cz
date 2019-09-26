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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4528ccd77fed2ea2a9b2d08243ffa1535bfad1ae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274089"
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
 Struktura je stejná jako struktura COR_VERSION, ale `CLR_DEBUGGING_VERSION` struktura poskytuje další pole verze struktury (`wStructVersion`). `CLR_DEBUGGING_VERSION` V současné době musí být toto pole nastaveno na hodnotu nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
