---
title: "EApiCategories – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 630a3048072ed7b19b3250e75aca3b31e4dd7df7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="eapicategories-enumeration"></a>EApiCategories – výčet
Popisuje kategorie funkcí, které hostitele může blokovat ve spuštění v částečně důvěryhodným kódem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eAll`|Určuje, že všechny spravované třídy a členové, které jsou předmětem dalších `EApiCategories` pole zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eExternalProcessMgmt`|Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a odstraňování externí procesů zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eExternalThreading`|Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a odstraňování externí vláken zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eMayLeakOnAbort`|Určuje, že spravované typy a členy, které může potenciálně nastat únik paměti na přerušení zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eNoCategory`|Určuje, že žádné kategorie spravovaného kódu zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eSecurityInfrastructure`|Určuje, že common language runtime (CLR) zabezpečení infrastructure blokovat používá částečně důvěryhodným kódem.|  
|`eSelfAffectingProcessMgmt`|Určuje, že spravované třídy a členy, jejichž možnosti může ovlivnit proces hostované zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eSelfAffectingThreading`|Určuje, že spravované třídy a členy, jejichž možnosti může ovlivnit vláken v procesu hostované zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eSharedState`|Určuje, že spravované třídy a členy, které zveřejňují sdíleného stavu zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eSynchronization`|Určuje, že common language runtime třídy a členů, které povolit uživatelský kód pro uložení zámky zablokovat spuštění v částečně důvěryhodným kódem.|  
|`eUI`|Určuje, že spravované třídy a členů, která povolují nebo vyžadovat zásahem ze strany zablokovat spuštění v částečně důvěryhodným kódem.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrhostprotectionmanager::setprotectedcategories –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda přebírá parametr typu `EApiCategories`.  
  
 `EApiCategories` – Výčet a `SetProtectedCategories` přímo souvisí s metoda na spravovaný <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> třídy. Spravované třídy se používá s <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> výčtu, jejichž hodnoty odpovídají přímo `EApiCategories` hodnoty k označení spravované typy a členy, které zveřejňují možnosti odpovídající kategorie popsaného `EApiCategories`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRHostProtectionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
