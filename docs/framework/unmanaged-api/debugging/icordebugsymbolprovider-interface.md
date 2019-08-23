---
title: ICorDebugSymbolProvider – rozhraní
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa30391f10a5f9540090e90500c1cb0a9a410b1e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955521"
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider – rozhraní
Poskytuje metody, které lze použít k načtení informací o symbolech ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAssemblyImageBytes – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Načte data ze sloučeného sestavení s ohledem na relativní virtuální adresu (RVA) ve sloučeném sestavení.|  
|[GetAssemblyImageMetadata – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Vrátí metadata ze sloučeného sestavení.|  
|[GetCodeRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Získá počáteční adresu a velikost metody dané relativní virtuální adresy (RVA) v metodě.|  
|[GetInstanceFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Načte symboly pole instance, které odpovídají token TypeSpec podpisu.|  
|[GetMergedAssemblyRecords – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Získá záznamy symbolů pro všechna Sloučená sestavení.|  
|[GetMethodLocalSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Načte místní symboly metody s relativní virtuální adresou (RVA) dané metody.|  
|[GetMethodParameterSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Načte symboly parametrů metody vzhledem k relativní virtuální adrese (RVA) dané metody.|  
|[GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Vrátí informace o vlastnostech metody, jako je token metadat metody a informace o jeho obecných parametrech, s ohledem na relativní virtuální adresu (RVA) v této metodě.|  
|[GetObjectSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Vrátí velikost objektu objektu na základě jeho signatury token TypeSpec.|  
|[GetStaticFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Získá symboly statického pole, které odpovídají token TypeSpec podpisu.|  
|[GetTypeProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Vrátí informace o vlastnostech typu, jako je například počet podpisů svých obecných parametrů, s ohledem na relativní virtuální adresu (RVA) v tabulce vtable.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
