---
title: HOST_TYPE – výčet
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
ms.openlocfilehash: e8dda83df8a320733f45dbcc13599cdf37d26492
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617149"
---
# <a name="host_type-enumeration"></a>HOST_TYPE – výčet
Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|Spusťte aplikaci z souboru applaunch. exe.<br /><br /> Tuto hodnotu použijte pro částečně důvěryhodné aplikace.|  
|`HOST_TYPE_CORFLAG`|Spusťte aplikaci přímo. To znamená, že aplikaci spustíte z vlastního souboru. exe.<br /><br /> Tuto hodnotu použijte pro plně důvěryhodné aplikace.|  
|`HOST_TYPE_DEFAULT`|Stejné jako HOST_TYPE_APPLAUNCH.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
