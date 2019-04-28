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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a313ea62455067fb36b94d942b0ce21589677e3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698158"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a>ICLRDebugging::OpenVirtualProcess – metoda
Získá icordebugprocess – rozhraní, která odpovídá common language runtime (CLR) modulu načtené v procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Základní adresa modul v cílovém procesu. COR_E_NOT_CLR bude vrácen, pokud zadaný modul není modul CLR.  
  
 `pDataTarget`  
 [in] Abstrakce cílové data, která umožňuje spravovanému ladicímu programu na kontrolu stavu procesu. Ladicí program musí implementovat [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní. Měli byste implementovat [iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) rozhraní pro zajištění podpory scénářů, kde není CLR, který je právě laděna nainstalovaný místně na počítači.  
  
 `pLibraryProvider`  
 [in] Rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje knihovnám ladění specifickým pro verzi k vyhledání a načtení na požádání. Tento parametr je povinný, jenom Pokud `ppProcess` nebo `pFlags` není `null`.  
  
 `pMaxDebuggerSupportedVersion`  
 [in] Nejvyšší verze modulu CLR, který lze ladit tímto ladicím programem. By měl určit hlavní, vedlejší verzi a vytvářet verze z nejnovější verze modulu CLR, který podporuje tento ladicí program a nastavit číslo revize 65535 tak, aby vyhovovaly budoucí místní CLR servisní verze.  
  
 `riidProcess`  
 [in] Icordebugprocess – rozhraní ID pro načtení. V současné době jsou pouze hodnoty IID_CORDEBUGPROCESS3 IID_CORDEBUGPROCESS2 a IID_CORDEBUGPROCESS.  
  
 `ppProcess`  
 [out] Ukazatel na rozhraní modelu COM, která je identifikovaná `riidProcess`.  
  
 `pVersion`  
 [out v] Verze modulu CLR. Na vstupu, tato hodnota může být `null`. Můžete také ukázat [clr_debugging_version –](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) struktury, v takovém případě struktura `wStructVersion` pole musí být inicializován na hodnotu 0 (nula).  
  
 Na výstupu vráceného `CLR_DEBUGGING_VERSION` struktura se vyplní informace o verzi CLR.  
  
 `pdwFlags`  
 [out] Informační příznaky o zadaného modulu runtime. Zobrazit [clr_debugging_process_flags –](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md) tématu Popis příznaky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pDataTarget` je `null`.|  
|CORDBG_E_LIBRARY_PROVIDER_ERROR|[Iclrdebugginglibraryprovider –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) zpětného volání vrátí chybu nebo neposkytuje platný popisovač.|  
|CORDBG_E_MISSING_DATA_TARGET_INTERFACE|`pDataTarget` neimplementuje rozhraní target požadovaná data pro tuto verzi modulu runtime.|  
|CORDBG_E_NOT_CLR|Zadaný modul není modul CLR. Hodnota HRESULT je také vrácen, když modul CLR nelze zjistit, že paměť byla poškozena, modul není k dispozici nebo verze CLR je novější než verze překrytí.|  
|CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL|Tuto verzi modulu runtime nepodporuje model ladění. V současné době nepodporuje model ladění CLR verze starší než [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. `pwszVersion` Výstupní parametr je stále nastaven na správnou hodnotu po této chybě.|  
|CORDBG_E_UNSUPPORTED_FORWARD_COMPAT|Verzi modulu CLR je vyšší než verze, které se na podporu deklarací identity tímto ladicím programem. `pwszVersion` Výstupní parametr je stále nastaven na správnou hodnotu po této chybě.|  
|E_NO_INTERFACE|`riidProcess` Rozhraní není k dispozici.|  
|CORDBG_E_UNSUPPORTED_VERSION_STRUCT|`CLR_DEBUGGING_VERSION` Struktura nemá rozpoznaná hodnota pro `wStructVersion`. Jediná akceptovaná hodnota v tuto chvíli je 0.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
