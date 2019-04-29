---
title: _EFN_StackTrace – funkce
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfbdbb389f9945ffeea649bcddd45bee8caf2496
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698314"
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace – funkce
Poskytuje textové vyjádření spravovaného zásobníku a pole `CONTEXT` záznamy, jeden pro každý přechod mezi nespravované a spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Client`  
 [in] Klient, který se právě ladí.  
  
 `wszTextOut`  
 [out] Textové vyjádření trasování zásobníku.  
  
 `puiTextLength`  
 [out] Ukazatel na počet znaků v `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Pole přechod kontexty.  
  
 `puiTransitionContextCount`  
 [out] Ukazatel na počet kontextů přechodu v poli.  
  
 `uiSizeOfContext`  
 [in] Velikost struktury kontextu.  
  
 `Flags`  
 [in] Nastavte na hodnotu 0 nebo SOS_STACKTRACE_SHOWADDRESSES (0x01) zobrazíte registru EBP a ukazatel zásobníku enter (ESP) před každou `module!functionname` řádku.  
  
## <a name="remarks"></a>Poznámky  
 `_EFN_StackTrace` Struktura může být volána z WinDbg programové rozhraní. Se používají následující parametry:  
  
- Pokud `wszTextOut` má hodnotu null a `puiTextLength` není null, funkce vrátí délku řetězce v `puiTextLength`.  
  
- Pokud `wszTextOut` je nenulová, uloží funkce text v `wszTextOut` až umístění indikován `puiTextLength`. Vrátí úspěšně Pokud byl dostatek volného místa ve vyrovnávací paměti nebo vrátí E_OUTOFMEMORY Pokud vyrovnávací paměť nebylo dostatečně dlouhé.  
  
- Přechod část funkce se ignoruje, pokud `pTransitionContexts` a `puiTransitionContextCount` mají obě hodnotu null. V tomto případě poskytuje funkci volajícím s textový výstup pouze názvy funkcí.  
  
- Pokud `pTransitionContexts` má hodnotu null a `puiTransitionContextCount` není null, funkce vrátí potřebný počet položek kontextu v `puiTransitionContextCount`.  
  
- Pokud `pTransitionContexts` není null, funkce zpracovává jako pole struktury délky `puiTransitionContextCount`. Velikost struktury je dán `uiSizeOfContext`, a musí mít velikost [simplecontext –](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) nebo `CONTEXT` pro architekturu.  
  
- `wszTextOut` je zapsán v následujícím formátu:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Pokud posun šestnáctkově 0x0, je zapsán bez posunutí.  
  
- Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí SOS_E_NOMANAGEDCODE.  
  
- `Flags` Parametru je 0 nebo SOS_STACKTRACE_SHOWADDRESSES zobrazíte EBP a ESP před každou `module!functionname` řádku. Ve výchozím nastavení je 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** SOS_Stacktrace.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
