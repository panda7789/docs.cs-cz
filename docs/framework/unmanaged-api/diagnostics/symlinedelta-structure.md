---
title: SYMLINEDELTA – struktura
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609297"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA – struktura
Poskytuje informace obslužné rutině symbolů o metodách, které byly přesunuty v důsledku úprav.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`mdMethod`|Token metadat metody.|  
|`delta`|Počet řádků, které byla metoda přesunuta.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl  
  
## <a name="see-also"></a>Viz také

- [Struktury úložiště symbolů diagnostiky](diagnostics-symbol-store-structures.md)
