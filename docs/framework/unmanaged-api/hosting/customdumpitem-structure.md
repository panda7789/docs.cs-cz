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
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138285"
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
|`itemKind`|Hodnota [ECustomDumpItemKind –](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) , která určuje druh položky, která má být přidána.|  
|`pReserved`|Aktuálně se nepoužívá. Všechny položky přidané do sjednocení nesmí být větší než velikost ukazatele. Pokud je vyžadován `struct`, je nutné jej přidělit samostatně a odkazovat na něj.|  
  
## <a name="remarks"></a>Poznámky  
 [ICLRErrorReportingManager:: BeginCustomDump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
