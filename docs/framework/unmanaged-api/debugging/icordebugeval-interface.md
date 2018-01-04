---
title: ICorDebugEval Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval
helpviewer_keywords: ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 77e97e31a20c392eebae1b373bb1af53f87c23e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval-interface1"></a>ICorDebugEval Interface1
Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Zruší výpočet to `ICorDebugEval` právě provádí objektu.|  
|[CallFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Nastaví volání zadanou funkci. (Zastaralé v rozhraní .NET Framework verze 2.0, pomocí [icordebugeval2::callparameterizedfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) místo.)|  
|[CreateValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Získá ukazatele rozhraní na "ICorDebugValue" objekt zadaného typu, s počáteční hodnotou nula nebo hodnotu null. (Zastaralé v rozhraní .NET Framework 2.0, pomocí [icordebugeval2::createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) místo.)|  
|[GetResult – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Získá ukazatele rozhraní k `ICorDebugValue` obsahující výsledky hodnocení.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Získá ukazatele rozhraní umožňuje "ICorDebugThread", kde toto testování provádí nebo spustí.|  
|[IsActive – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Získá hodnotu, která určuje, jestli to `ICorDebugEval` objekt právě probíhá.|  
|[NewArray – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Přiděluje nový pole typu zadaného elementu a dimenze. (Zastaralé v rozhraní .NET Framework 2.0, pomocí [icordebugeval2::newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) místo.)|  
|[NewObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Přidělí nové instance objektu a volá metodu zadané konstruktor. (Zastaralé v rozhraní .NET Framework 2.0, pomocí [icordebugeval2::newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) místo.)|  
|[NewObjectNoConstructor – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Bez pokus o volání metody konstruktoru přiděluje novou instanci objektu zadaného typu. (Zastaralé v rozhraní .NET Framework 2.0, pomocí [icordebugeval2::newparameterizedobjectnoconstructor –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) místo.)|  
|[NewString – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Přiděluje nový objekt řetězce s zadaný obsah.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugEval` Objekt se vytvoří v rámci konkrétní vlákno, které se používá k provádění hodnocení. Všechny objekty a typy používaných v daném vyhodnocení se musí nacházet ve stejné doméně aplikace. Tuto doménu aplikace nemusí být stejný jako aktuální doménu aplikace vlákna. Hodnocení mohou být použity.  
  
 Po vyhodnocení operace nejsou dokončeny dokud volání ladicí program [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)a pak obdrží [icordebugmanagedcallback::evalcomplete –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) zpětného volání. Pokud potřebujete použít funkci vyhodnocení bez povolení dalších podprocesů pro spuštění, pozastavení vláken pomocí [icordebugcontroller::setallthreadsdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) nebo [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Vzhledem k tomu, že uživatelský kód běží, když probíhá vyhodnocení, může dojít všechny události, ladění, včetně třída zatížení a zarážky. Zpětná volání, jako za normálních okolností, aby se tyto události se zobrazí ladicího programu. Jako součást kontroly stavu normální program se zobrazí stav vyhodnocení. Řetězec zásobníku se `CHAIN_FUNC_EVAL` řetězu (najdete v části "CorDebugStepReason" – výčet a [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda). Úplné ladicího programu rozhraní API bude nadále fungovat normálně.  
  
 Pokud nastane zablokovaných nebo nekonečné opakování situace může dokončit nikdy uživatelského kódu. V takovém případě musí volat [icordebugeval::Abort –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) před obnovením program.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
    
    
    
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
