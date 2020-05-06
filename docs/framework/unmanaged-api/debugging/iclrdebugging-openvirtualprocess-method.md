---
title: ICLRDebugging::OpenVirtualProcess – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 1598130eb097655d3e83689956eb3614103eb573
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860377"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess – metoda
Získá rozhraní ICorDebugProcess, které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleBaseAddress`  
 pro Základní adresa modulu v cílovém procesu. Pokud zadaný modul není modul CLR, vrátí se COR_E_NOT_CLR.  
  
 `pDataTarget`  
 pro Abstrakce cíle dat, která umožňuje spravovanému ladicímu programu zkontrolovat stav procesu. Ladicí program musí implementovat rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) . Rozhraní [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) byste měli implementovat pro podporu scénářů, ve kterých se modul CLR, který právě ladíte, nenainstaluje místně na počítači.  
  
 `pLibraryProvider`  
 pro Rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění specifických pro konkrétní verzi na vyžádání. Tento parametr je vyžadován pouze v `ppProcess` případě `pFlags` , že `null`není.  
  
 `pMaxDebuggerSupportedVersion`  
 pro Nejvyšší verze CLR, kterou tento ladicí program může ladit. Měli byste zadat hlavní, vedlejší a buildové verze z nejnovější verze CLR, kterou tento ladicí program podporuje, a nastavit číslo revize na 65535 pro budoucí místní verze údržby CLR.  
  
 `riidProcess`  
 pro ID rozhraní ICorDebugProcess, které se má načíst V současné době jsou k disIID_CORDEBUGPROCESS3 pouze přijatelné hodnoty, IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 mimo Ukazatel na rozhraní modelu COM, které je identifikováno `riidProcess`.  
  
 `pVersion`  
 [in, out] Verze modulu CLR. U vstupu může být `null`tato hodnota. Může také ukazovat na strukturu [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) . v takovém případě musí být `wStructVersion` pole struktury inicializováno na hodnotu 0 (nula).  
  
 Ve výstupu se vrácená `CLR_DEBUGGING_VERSION` struktura vyplní informacemi o verzi pro modul CLR.  
  
 `pdwFlags`  
 mimo Informační příznaky zadaného modulu runtime. Popis příznaků najdete v tématu věnovaném [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pDataTarget` je `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Zpětné volání [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) vrací chybu nebo neposkytuje platný popisovač.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget`neimplementuje požadovaná cílová rozhraní dat pro tuto verzi modulu runtime.|  
|CORDBG_E_NOT_CLR|Uvedený modul není modul CLR. Tato hodnota HRESULT je vrácena také v případě, že modul CLR nelze zjistit, protože paměť je poškozena, modul není k dispozici nebo je verze CLR novější než verze Shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Tato verze modulu runtime nepodporuje tento ladicí model. Model ladění není aktuálně podporován verzemi CLR před .NET Framework 4. Po `pwszVersion` této chybě je výstupní parametr stále nastaven na správnou hodnotu.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Verze modulu CLR je vyšší než verze, které tento ladicí program vyžaduje pro podporu. Po `pwszVersion` této chybě je výstupní parametr stále nastaven na správnou hodnotu.|  
|E_NO_INTERFACE|`riidProcess` Rozhraní není k dispozici.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Struktura neobsahuje rozpoznanou hodnotu pro `wStructVersion`. Jediná přijatá hodnota je v tomto okamžiku 0.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
