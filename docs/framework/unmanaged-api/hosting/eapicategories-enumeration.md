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
ms.openlocfilehash: d31b0190ef9a697fb27c849db080bec6c57618ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616382"
---
# <a name="eapicategories-enumeration"></a>EApiCategories – výčet
Popisuje kategorie schopností, které může hostitel zablokovat, aby běžel v částečně důvěryhodném kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`eAll`|Určuje, že všechny spravované třídy a členy, které jsou pokryté ostatními `EApiCategories` poli, se mají zablokovat spouštění v částečně důvěryhodném kódu.|  
|`eExternalProcessMgmt`|Určuje, že spravované třídy a členy, které umožňují vytvoření, manipulaci a zničení externích procesů, se mají zablokovat spouštění v částečně důvěryhodném kódu.|  
|`eExternalThreading`|Určuje, že spravované třídy a členy, které umožňují vytvoření, manipulaci a zničení externích vláken, budou zablokovány spuštění v částečně důvěryhodném kódu.|  
|`eMayLeakOnAbort`|Určuje, že spravované typy a členy, které by mohly způsobit nevracení paměti při přerušení, se zablokují pro spuštění v částečně důvěryhodném kódu.|  
|`eNoCategory`|Určuje, že žádné kategorie spravovaného kódu není možné zablokovat spuštění v částečně důvěryhodném kódu.|  
|`eSecurityInfrastructure`|Určuje, že infrastruktura zabezpečení modulu CLR (Common Language Runtime) je zablokovaná pro použití částečně důvěryhodným kódem.|  
|`eSelfAffectingProcessMgmt`|Určuje, že spravované třídy a členy, jejichž schopnosti mohou ovlivnit hostovaný proces, mají zablokovaný běh v částečně důvěryhodném kódu.|  
|`eSelfAffectingThreading`|Určuje, že spravované třídy a členy, jejichž schopnosti mohou ovlivnit vlákna v hostovaném procesu, jsou zablokovány pro spuštění v částečně důvěryhodném kódu.|  
|`eSharedState`|Určuje, že spravované třídy a členy, které zveřejňují sdílený stav, budou zablokovány spuštění v částečně důvěryhodném kódu.|  
|`eSynchronization`|Určuje, že se mají blokované třídy a členy společného jazykového modulu runtime, které umožňují blokovat zámkům, blokovat spuštění v částečně důvěryhodném kódu.|  
|`eUI`|Určuje, že spravované třídy a členy, které povolují nebo vyžadují lidskou interakci, se zablokují, aby se spustily v částečně důvěryhodném kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICLRHostProtectionManager:: SetProtectedCategories –](iclrhostprotectionmanager-setprotectedcategories-method.md) přebírá parametr typu `EApiCategories` .  
  
 `EApiCategories`Výčet a `SetProtectedCategories` Metoda přímo souvisí se spravovanou <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> třídou. Spravovaná třída se používá společně s <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> výčtem, jejichž hodnoty odpovídají přímo `EApiCategories` hodnotám, pro označení spravovaných typů a členů, které zpřístupňují funkce odpovídající kategoriím popsaným v `EApiCategories` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRHostProtectionManager – rozhraní](iclrhostprotectionmanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
