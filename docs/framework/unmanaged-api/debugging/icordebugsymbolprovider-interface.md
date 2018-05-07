---
title: ICorDebugSymbolProvider rozhraní
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e9f475ee3c46b8abb94ce7f804cc8b4a8054ec2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovider-interface"></a>ICorDebugSymbolProvider rozhraní
Poskytuje metody, které lze použít k načtení informací o symbolu ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAssemblyImageBytes – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagebytes-method.md)|Čte data z sloučené sestavení zadaný relativní virtuální adresy (RVA) v sloučené sestavení.|  
|[GetAssemblyImageMetadata – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getassemblyimagemetadata-method.md)|Vrátí metadata z sloučené sestavení.|  
|[GetCodeRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getcoderange-method.md)|Získá metoda počáteční adresy a velikost relativní virtuální adresy (RVA) v metodu.|  
|[GetInstanceFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)|Získá instanci symbolů pole, které odpovídají typ typespec podpis.|  
|[GetMergedAssemblyRecords – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmergedassemblyrecords-method.md)|Získá záznamy symbol pro sloučené sestavení.|  
|[GetMethodLocalSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)|Získá symboly místní metoda zadaný relativní virtuální adresa (RVA) této metody.|  
|[GetMethodParameterSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)|Získá symboly metoda parametr zadaný relativní virtuální adresa (RVA) této metody.|  
|[GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)|Zadaná relativní virtuální adresy (RVA) v dané metody vrací informace o vlastnosti metoda, například metadata token a informace o jeho obecné parametry metody.|  
|[GetObjectSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getobjectsize-method.md)|Vrátí velikost objektu pro objekt podle jeho typ typespec podpis.|  
|[GetStaticFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)|Získá symboly statické pole, které odpovídají typ typespec podpis.|  
|[GetTypeProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)|Zadaný relativní virtuální adresy (RVA) v tabulce vtable vrací informace o vlastnosti typ, například počet podpis jeho obecné parametry.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní je k dispozici s .NET Native jenom. Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
