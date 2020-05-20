---
title: EClrUnhandledException – výčet
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 63b07dda2293d3e05bd3c8fcdc45f20a498ea54c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616304"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException – výčet
Popisuje dostupné možnosti pro správu výjimek, které jsou v uživatelském kódu neošetřené.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|Určuje, že dojde k výchozímu chování. Proces se odpojí.|  
|`eHostDeterminedPolicy`|Určuje, že modul CLR (Common Language Runtime) ignoruje neošetřené výjimky a umožňuje hostiteli určit jakoukoli další akci.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit, že se CLR chová jako starší verze, použijte `eHostDeterminedPolicy` člena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EClrFailure – výčet](eclrfailure-enumeration.md)
- [EClrOperation – výčet](eclroperation-enumeration.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy – metoda](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager – rozhraní](ihostpolicymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
