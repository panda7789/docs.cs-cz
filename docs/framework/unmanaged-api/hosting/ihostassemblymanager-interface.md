---
title: IHostAssemblyManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 4e32a36a4cf751bf7c5a2c918fde0122f21b7878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501586"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager – rozhraní
Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR (Common Language Runtime) nebo hostitelem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetAssemblyStore – metoda](ihostassemblymanager-getassemblystore-method.md)|Získá ukazatel rozhraní na [IHostAssemblyStore](ihostassemblystore-interface.md) , který představuje seznam sestavení načtených hostitelem.|  
|[GetNonHostStoreAssemblies – metoda](ihostassemblymanager-getnonhoststoreassemblies-method.md)|Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel není vyžadován k implementaci `IHostAssemblyManager` nebo `IHostAssemblyStore` . Pokud hostitel implementuje `IHostAssemblyManager` , musí také implementovat `IHostAssemblyStore` .  
  
 Běhové dotazy pro `IHostAssemblyManager` volání metody [IHostControl:: GetHostManager –](ihostcontrol-gethostmanager-method.md) při inicializaci s `IID` IID_IHostAssemblyManager.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
