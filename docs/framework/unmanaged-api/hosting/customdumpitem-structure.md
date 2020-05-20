---
title: CustomDumpItem – struktura
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616434"
---
# <a name="customdumpitem-structure"></a>CustomDumpItem – struktura
Popisuje položku, která se má přidat do vlastního výpisu paměti při zasílání zpráv o chybách.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`itemKind`|Hodnota [ECustomDumpItemKind –](ecustomdumpitemkind-enumeration.md) , která určuje druh položky, která má být přidána.|  
|`pReserved`|Aktuálně se nepoužívá. Všechny položky přidané do sjednocení nesmí být větší než velikost ukazatele. Pokud `struct` je vyžadován, je nutné jej přidělit samostatně a odkazovat na něj.|  
  
## <a name="remarks"></a>Poznámky  
 [ICLRErrorReportingManager:: BeginCustomDump –](iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro hostování](hosting-structures.md)
