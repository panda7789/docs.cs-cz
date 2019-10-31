---
title: ICorDebugEval – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: 33b1afca0b7b662cb7f922e20ba0d6d614c319f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085031"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval – rozhraní

Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Přeruší výpočet, který tento objekt `ICorDebugEval` právě provádí.|  
|[CallFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Nastaví volání zadané funkce. (Zastaralé ve verzi .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: CallParameterizedFunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) .)|  
|[CreateValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Získá ukazatel rozhraní na objekt "ICorDebugValue" zadaného typu s počáteční hodnotou 0 nebo null. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) .)|  
|[GetResult – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Získá ukazatel rozhraní na `ICorDebugValue`, která obsahuje výsledky vyhodnocení.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Získá ukazatel rozhraní na "ICorDebugThread", kde toto vyhodnocení provádí nebo spustí.|  
|[IsActive – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Získá hodnotu, která označuje, zda je tento objekt `ICorDebugEval` aktuálně spuštěn.|  
|[NewArray – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Přidělí nové pole zadaného typu a dimenzí prvku. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) .)|  
|[NewObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Přidělí novou instanci objektu a zavolá specifikovanou metodu konstruktoru. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) .)|  
|[NewObjectNoConstructor – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Přidělí novou instanci objektu zadaného typu bez pokusu o volání metody konstruktoru. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: NewParameterizedObjectNoConstructor –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) .)|  
|[NewString – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Přidělí nový objekt řetězce se zadaným obsahem.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt `ICorDebugEval` je vytvořen v kontextu konkrétního vlákna, které se používá k provedení vyhodnocení. Všechny objekty a typy používané v daném vyhodnocení musí být umístěny ve stejné doméně aplikace. Doména aplikace nemusí být stejná jako aktuální doména aplikace vlákna. Hodnocení lze vnořovat.  
  
 Operace vyhodnocení nejsou dokončeny, dokud ladicí program nevolá metodu [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)a poté obdrží zpětné volání [ICorDebugManagedCallback:: EvalComplete –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) . Pokud potřebujete použít funkci hodnocení bez povolení spuštění jiných vláken, pozastavte vlákna pomocí [ICorDebugController:: SetAllThreadsDebugState –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) nebo [ICorDebugController:: stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md) před voláním [. ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Vzhledem k tomu, že uživatelský kód je spuštěn, když probíhá vyhodnocení, může dojít k jakýmkoli událostem ladění, včetně načtených tříd a zarážek. Ladicí program bude pro tyto události přijímat zpětná volání jako normální. Stav vyhodnocení bude zobrazen jako součást kontroly normálního stavu programu. Řetěz zásobníku bude `CHAIN_FUNC_EVAL` řetězu (viz "výčet" CorDebugStepReason – a metoda [ICorDebugChain:: getdůvod](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) ). Úplné rozhraní API ladicího programu bude i nadále fungovat jako normální.  
  
 Pokud dojde k zablokování nebo nekonečné situaci ve smyčce, nemusí být kód uživatele nikdy dokončen. V takovém případě je nutné volat [ICorDebugEval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) před pokračováním programu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
