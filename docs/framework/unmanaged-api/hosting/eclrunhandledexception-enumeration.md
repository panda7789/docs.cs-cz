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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e5fb3ab1d2dedb220fd4a486409512414233021
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176667"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException – výčet
Popisuje dostupné možnosti pro správu výjimek, které se neošetří v uživatelském kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|Určuje, že dochází k výchozí chování. Proces iframeworkview.|  
|`eHostDeterminedPolicy`|Určuje, že common language runtime (CLR) ignoruje neošetřené výjimky a tato funkce umožňuje hostiteli zjistit žádnou další akci.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit, že modul CLR se chovají jako předchozí verze, použijte `eHostDeterminedPolicy` člena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
