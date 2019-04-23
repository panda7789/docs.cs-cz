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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58c9d4c66af0bb9f4e66d17b18ac78ef8271bc31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072659"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo – struktura

Představuje jediný neodkazovaný blok kódu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`startAddr`|A `CORDB_ADDRESS` hodnotu, která určuje počáteční adresu bloků.|  
|`length`|Velikost v bajtech, bloků.|  
  
## <a name="remarks"></a>Poznámky  
 Jediný neodkazovaný blok kódu je oblast nativní kód, který je součástí objektu kódu, jako je například funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCodeChunks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
