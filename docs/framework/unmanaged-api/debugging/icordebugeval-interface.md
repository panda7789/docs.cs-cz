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
ms.openlocfilehash: f13cd6d6cae5bae0c51674e00f275a2c4853c915
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976223"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval – rozhraní

Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](icordebugeval-abort-method.md)|Přeruší výpočet, který `ICorDebugEval` tento objekt právě provádí.|  
|[CallFunction – metoda](icordebugeval-callfunction-method.md)|Nastaví volání zadané funkce. (Zastaralé ve verzi .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: CallParameterizedFunction –](icordebugeval2-callparameterizedfunction-method.md) .)|  
|[CreateValue – metoda](icordebugeval-createvalue-method.md)|Získá ukazatel rozhraní na objekt "ICorDebugValue" zadaného typu s počáteční hodnotou 0 nebo null. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: createvaluefortype –](icordebugeval2-createvaluefortype-method.md) .)|  
|[GetResult – metoda](icordebugeval-getresult-method.md)|Získá ukazatel rozhraní `ICorDebugValue` , které obsahuje výsledky vyhodnocení.|  
|[GetThread – metoda](icordebugeval-getthread-method.md)|Získá ukazatel rozhraní na "ICorDebugThread", kde toto vyhodnocení provádí nebo spustí.|  
|[IsActive – metoda](icordebugeval-isactive-method.md)|Získá hodnotu, která označuje, zda `ICorDebugEval` je tento objekt aktuálně spuštěn.|  
|[NewArray – metoda](icordebugeval-newarray-method.md)|Přidělí nové pole zadaného typu a dimenzí prvku. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: newparameterizedarray –](icordebugeval2-newparameterizedarray-method.md) .)|  
|[NewObject – metoda](icordebugeval-newobject-method.md)|Přidělí novou instanci objektu a zavolá specifikovanou metodu konstruktoru. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: newparameterizedobject –](icordebugeval2-newparameterizedobject-method.md) .)|  
|[NewObjectNoConstructor – metoda](icordebugeval-newobjectnoconstructor-method.md)|Přidělí novou instanci objektu zadaného typu bez pokusu o volání metody konstruktoru. (Zastaralé v .NET Framework 2,0; místo toho použijte [ICorDebugEval2:: NewParameterizedObjectNoConstructor –](icordebugeval2-newparameterizedobjectnoconstructor-method.md) .)|  
|[NewString – metoda](icordebugeval-newstring-method.md)|Přidělí nový objekt řetězce se zadaným obsahem.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugEval` Objekt je vytvořen v kontextu konkrétního vlákna, které se používá k provedení vyhodnocení. Všechny objekty a typy používané v daném vyhodnocení musí být umístěny ve stejné doméně aplikace. Doména aplikace nemusí být stejná jako aktuální doména aplikace vlákna. Hodnocení lze vnořovat.  
  
 Operace vyhodnocení nejsou dokončeny, dokud ladicí program nevolá metodu [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)a poté obdrží zpětné volání [ICorDebugManagedCallback:: EvalComplete –](icordebugmanagedcallback-evalcomplete-method.md) . Pokud potřebujete použít funkci hodnocení bez povolení spuštění jiných vláken, pozastavte vlákna pomocí [ICorDebugController:: SetAllThreadsDebugState –](icordebugcontroller-setallthreadsdebugstate-method.md) nebo [ICorDebugController:: stop](icordebugcontroller-stop-method.md) před voláním metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).  
  
 Vzhledem k tomu, že uživatelský kód je spuštěn, když probíhá vyhodnocení, může dojít k jakýmkoli událostem ladění, včetně načtených tříd a zarážek. Ladicí program bude pro tyto události přijímat zpětná volání jako normální. Stav vyhodnocení bude zobrazen jako součást kontroly normálního stavu programu. Řetěz zásobníku bude `CHAIN_FUNC_EVAL` řetěz (viz "výčet" CorDebugStepReason – a metoda [ICorDebugChain:: getdůvod](icordebugchain-getreason-method.md) ). Úplné rozhraní API ladicího programu bude i nadále fungovat jako normální.  
  
 Pokud dojde k zablokování nebo nekonečné situaci ve smyčce, nemusí být kód uživatele nikdy dokončen. V takovém případě je nutné volat [ICorDebugEval:: Abort](icordebugeval-abort-method.md) před pokračováním programu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
