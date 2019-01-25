---
title: EApiCategories – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50aa116fc1f5377254a8a6a128d0240c57cb52b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597564"
---
# <a name="eapicategories-enumeration"></a>EApiCategories – výčet
Popisuje kategorie funkcí, které hostitele může blokovat spouštění v částečně důvěryhodným kódem.  
  
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
|`eAll`|Určuje, že všechny spravované třídy a členy, které jsou zahrnuté do jiné `EApiCategories` pole zablokováno v částečně důvěryhodným kódem.|  
|`eExternalProcessMgmt`|Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a zničení procesů, externím zablokováno v částečně důvěryhodným kódem.|  
|`eExternalThreading`|Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a zničení externí vláken zablokováno v částečně důvěryhodným kódem.|  
|`eMayLeakOnAbort`|Určuje, že spravované typy a členy, které může potenciálně způsobit únik paměti při přerušení zablokováno v částečně důvěryhodným kódem.|  
|`eNoCategory`|Určuje, že žádný spravovaný kód kategorie zablokováno v částečně důvěryhodným kódem.|  
|`eSecurityInfrastructure`|Určuje, že common language runtime (CLR) zabezpečení infrastructure být blokovány z používán částečně důvěryhodným kódem.|  
|`eSelfAffectingProcessMgmt`|Určuje, že spravované třídy a členy, jejichž schopnosti může ovlivnit proces hostované zablokováno v částečně důvěryhodným kódem.|  
|`eSelfAffectingThreading`|Určuje, že spravované třídy a členy, jejichž funkce může mít vliv na vlákna v procesu hostované zablokováno v částečně důvěryhodným kódem.|  
|`eSharedState`|Určuje, že spravované třídy a členy, které zpřístupňují sdílený stav zablokováno v částečně důvěryhodným kódem.|  
|`eSynchronization`|Určuje, že common language runtime třídy a členy, které umožňují uživatelský kód pro uložení zámky zablokováno v částečně důvěryhodným kódem.|  
|`eUI`|Určuje, že spravovaných tříd a členů, která povolují nebo vyžadují zásahem ze strany zablokováno v částečně důvěryhodným kódem.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrhostprotectionmanager::setprotectedcategories –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda přijímá parametr typu `EApiCategories`.  
  
 `EApiCategories` Výčet a `SetProtectedCategories` přímo souvisí s metoda na spravovanou <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> třídy. Spravovaná třída se používá s <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> výčtu, jehož hodnoty odpovídají přímo `EApiCategories` hodnoty k označení spravované typy a členy, které ukazují možnosti odpovídající kategorie popsal `EApiCategories`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRHostProtectionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
