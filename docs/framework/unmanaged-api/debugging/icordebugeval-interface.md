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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 745917af176de47999737c87833c23df9c75ea7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080862"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval – rozhraní

Poskytuje metody povolující ladicímu programu spouštět kód v kontextu laděného kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Zruší výpočtu to `ICorDebugEval` objektu v tuto chvíli provádí.|  
|[CallFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Nastaví zadanou funkci volání. (Zastaralé v rozhraní .NET Framework verze 2.0; použijte [icordebugeval2::callparameterizedfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) místo.)|  
|[CreateValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Získá ukazatel rozhraní na "ICorDebugValue" objekt zadaného typu, s počáteční hodnotou nula nebo hodnotu null. (Zastaralé v rozhraní .NET Framework 2.0; použijte [icordebugeval2::createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) místo.)|  
|[GetResult – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Získá ukazatel rozhraní k `ICorDebugValue` , která obsahuje výsledky hodnocení.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Získá ukazatel rozhraní "ICorDebugThread", kde se toto vyhodnocení provádí nebo spustí.|  
|[IsActive – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Získá hodnotu, která určuje, jestli to `ICorDebugEval` objekt aktuálně spouští.|  
|[NewArray – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Přidělí nové pole typu zadaného elementu a dimenze. (Zastaralé v rozhraní .NET Framework 2.0; použijte [icordebugeval2::newparameterizedarray –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) místo.)|  
|[NewObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Přidělí novou instanci objektu a volá metodu zadaný konstruktor. (Zastaralé v rozhraní .NET Framework 2.0; použijte [icordebugeval2::newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) místo.)|  
|[NewObjectNoConstructor – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Přidělí novou instanci objektu zadaného typu, bez pokusu o volání metody konstruktoru. (Zastaralé v rozhraní .NET Framework 2.0; použijte [icordebugeval2::newparameterizedobjectnoconstructor –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) místo.)|  
|[NewString – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Přidělí nový řetězec objekt se zadaným obsahem.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugEval` Objekt je vytvořen v kontextu konkrétní vlákno, které se používá k provedení vyhodnocení. Všechny objekty a typy použité v daném hodnocení se musí nacházet ve stejné doméně aplikace. Tuto doménu aplikace nemusí být stejný jako aktuální domény aplikace vlákna. Mohou být vnořené hodnocení.  
  
 Operace hodnocení nedokončí až do volání ladicího programu [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)a potom přijímá [icordebugmanagedcallback::evalcomplete –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) zpětného volání. Pokud potřebujete použít funkci vyhodnocení bez povolení jiných podprocesů pro spuštění, pozastavení vláken pomocí [icordebugcontroller::setallthreadsdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) nebo [icordebugcontroller::stop –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Vzhledem k tomu, že uživatelský kód běží, když probíhá vyhodnocení, může dojít všechny výjimky ladění, včetně načtení třídy a zarážky. Ladicí program se zobrazí jako za normálních okolností, tyto události zpětná volání. Jako součást kontroly stavu normální programu se zobrazí stav vyhodnocení. Řetěz zásobníku bude `CHAIN_FUNC_EVAL` řetězce (naleznete v tématu "Cordebugstepreason –" výčet a [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda). Úplné ladicí program rozhraní API bude nadále fungovat jako obvykle.  
  
 Pokud jeví jako zablokované nebo nekonečné smyčky situace nastane, může dokončení nikdy uživatelského kódu. V takovém případě je nutné volat [icordebugeval::Abort –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) před obnovením program.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
