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
ms.openlocfilehash: cd43dce995c2bc9a45a0c8134a91b20cb1dec26e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111431"
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
 pro Základní adresa modulu v cílovém procesu. COR_E_NOT_CLR se vrátí, pokud zadaný modul není modul CLR.  
  
 `pDataTarget`  
 pro Abstrakce cíle dat, která umožňuje spravovanému ladicímu programu zkontrolovat stav procesu. Ladicí program musí implementovat rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) . Rozhraní [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) byste měli implementovat pro podporu scénářů, ve kterých se modul CLR, který právě ladíte, nenainstaluje místně na počítači.  
  
 `pLibraryProvider`  
 pro Rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění specifických pro konkrétní verzi na vyžádání. Tento parametr je vyžadován pouze v případě, že `ppProcess` nebo `pFlags` není `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 pro Nejvyšší verze CLR, kterou tento ladicí program může ladit. Měli byste zadat hlavní, vedlejší a buildové verze z nejnovější verze CLR, kterou tento ladicí program podporuje, a nastavit číslo revize na 65535 pro budoucí místní verze údržby CLR.  
  
 `riidProcess`  
 pro ID rozhraní ICorDebugProcess, které se má načíst V současné době jediné přijatelné hodnoty jsou IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 mimo Ukazatel na rozhraní COM identifikované `riidProcess`.  
  
 `pVersion`  
 [in, out] Verze modulu CLR. U vstupu může být tato hodnota `null`. Může také ukazovat na strukturu [CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) . v takovém případě musí být pole `wStructVersion` struktury inicializováno na hodnotu 0 (nula).  
  
 Ve výstupu se vrácená `CLR_DEBUGGING_VERSION` struktura vyplní informacemi o verzi pro modul CLR.  
  
 `pdwFlags`  
 mimo Informační příznaky zadaného modulu runtime. Popis příznaků najdete v tématu [CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pDataTarget` je `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|Zpětné volání [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) vrací chybu nebo neposkytuje platný popisovač.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` neimplementuje požadovaná cílová rozhraní dat pro tuto verzi modulu runtime.|  
|CORDBG_E_NOT_CLR|Uvedený modul není modul CLR. Tato hodnota HRESULT je vrácena také v případě, že modul CLR nelze zjistit, protože paměť je poškozena, modul není k dispozici nebo je verze CLR novější než verze Shim.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Tato verze modulu runtime nepodporuje tento ladicí model. Model ladění není aktuálně podporován verzemi CLR před .NET Framework 4. Výstupní parametr `pwszVersion` je po této chybě stále nastaven na správnou hodnotu.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Verze modulu CLR je vyšší než verze, které tento ladicí program vyžaduje pro podporu. Výstupní parametr `pwszVersion` je po této chybě stále nastaven na správnou hodnotu.|  
|E_NO_INTERFACE|Rozhraní `riidProcess` není k dispozici.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|Struktura `CLR_DEBUGGING_VERSION` nemá rozpoznanou hodnotu pro `wStructVersion`. Jediná přijatá hodnota je v tomto okamžiku 0.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
