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
ms.openlocfilehash: 9035d9a53c4b0c8822b79e641aef092b4a48c418
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895043"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_– funkce trasování zásobníku
Poskytuje textovou reprezentaci spravovaného trasování zásobníku a pole `CONTEXT` záznamů, jednu pro každý přechod mezi nespravovaným a spravovaným kódem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Probíhá ladění klienta.  
  
 `wszTextOut`  
 mimo Textová reprezentace trasování zásobníku.  
  
 `puiTextLength`  
 mimo Ukazatel na počet znaků v `wszTextOut`.  
  
 `pTransitionContexts`  
 mimo Pole kontextů přechodu.  
  
 `puiTransitionContextCount`  
 mimo Ukazatel na počet kontextů přechodu v poli.  
  
 `uiSizeOfContext`  
 pro Velikost struktury kontextu.  
  
 `Flags`  
 pro Nastavte na hodnotu 0 nebo SOS_STACKTRACE_SHOWADDRESSES (0x01), aby se zobrazil registr EBP a jako ukazatel na zadání zásobníku (ESP) před každým `module!functionname` řádkem.  
  
## <a name="remarks"></a>Poznámky  
 `_EFN_StackTrace` Struktura může být volána z programového rozhraní WinDbg. Parametry se používají takto:  
  
- Pokud `wszTextOut` má hodnotu null `puiTextLength` a není null, funkce vrátí délku řetězce v `puiTextLength`.  
  
- Pokud `wszTextOut` není null, funkce ukládá `wszTextOut` text až `puiTextLength`do umístění, které je uvedeno v. Pokud byla ve vyrovnávací paměti dostatek místa, vrátí se úspěšně, nebo pokud vyrovnávací paměť není dost velká, vrátí E_OUTOFMEMORY.  
  
- Část přechodu funkce je ignorována, pokud `pTransitionContexts` a `puiTransitionContextCount` jsou obě hodnoty null. V tomto případě funkce poskytuje volajícím textový výstup pouze názvů funkcí.  
  
- Pokud `pTransitionContexts` má hodnotu null `puiTransitionContextCount` a není null, funkce vrátí potřebný počet kontextových položek v `puiTransitionContextCount`.  
  
- Pokud `pTransitionContexts` hodnota není null, funkce ji zpracuje jako pole struktury délky `puiTransitionContextCount`. Velikost struktury je dána `uiSizeOfContext`, a musí se jednat o velikost [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) nebo `CONTEXT` pro architekturu.  
  
- `wszTextOut`je zapsán v následujícím formátu:  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Pokud je posun v šestnáctkové soustavě 0x0, není zapsán žádný posun.  
  
- Pokud není ve vlákně aktuálně v kontextu žádný spravovaný kód, funkce vrátí SOS_E_NOMANAGEDCODE.  
  
- Parametr je buď 0, nebo SOS_STACKTRACE_SHOWADDRESSES, aby se zobrazily EBP a ESP před `module!functionname` každým řádkem. `Flags` Ve výchozím nastavení má hodnotu 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** SOS_Stacktrace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
