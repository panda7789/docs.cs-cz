---
title: CodeChunkInfo – struktura
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132390"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo – struktura

Představuje jeden blok kódu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`startAddr`|Hodnota `CORDB_ADDRESS`, která určuje počáteční adresu bloku.|  
|`length`|Velikost bloku (v bajtech).|  
  
## <a name="remarks"></a>Poznámky  
 Jediný blok kódu je oblast nativního kódu, který je součástí objektu kódu, jako je například funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCodeChunks – metoda](icordebugcode2-getcodechunks-method.md)
- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
