---
title: "_EFN_StackTrace – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_StackTrace
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_StackTrace
helpviewer_keywords: _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 031812b2c286c5647afb9c88882f22e2c7c3addf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace – funkce
Poskytuje textové reprezentace trasování spravované zásobníku a pole `CONTEXT` zaznamenává, jednu pro každý přechod mezi nespravované a spravované kódu.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `Client`  
 [v] Klient laděné.  
  
 `wszTextOut`  
 [out] Reprezentace textu trasování zásobníku.  
  
 `puiTextLength`  
 [out] Ukazatel na počet znaků v `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Pole kontexty přechodu.  
  
 `puiTransitionContextCount`  
 [out] Ukazatel na počet přechod kontexty v poli.  
  
 `uiSizeOfContext`  
 [v] Velikost strukturu kontextu.  
  
 `Flags`  
 [v] Nastavte na hodnotu 0 nebo SOS_STACKTRACE_SHOWADDRESSES (0x01) pro zobrazení EBP registrace a ukazatel zásobníku enter (ESP) před každou `module!functionname` řádku.  
  
## <a name="remarks"></a>Poznámky  
 `_EFN_StackTrace` Struktura lze volat z WinDbg programovací rozhraní. Parametry se používají následujícím způsobem:  
  
-   Pokud `wszTextOut` má hodnotu null a `puiTextLength` je hodnotou not null, funkce vrátí hodnotu délka řetězce v `puiTextLength`.  
  
-   Pokud `wszTextOut` je hodnotou not null, funkce ukládá textu v `wszTextOut` až do umístění určeného v `puiTextLength`. Vrátí úspěšně Pokud byl dostatek místa ve vyrovnávací paměti nebo vrátí E_OUTOFMEMORY Pokud vyrovnávací paměť nebylo dost dlouhé.  
  
-   Část přechod funkce je ignorována, pokud `pTransitionContexts` a `puiTransitionContextCount` jsou oba hodnotu null. V takovém případě funkce poskytuje volající s textového výstupu pouze názvy funkcí.  
  
-   Pokud `pTransitionContexts` má hodnotu null a `puiTransitionContextCount` je hodnotou not null, funkce vrátí hodnotu potřebný počet položek kontextu v `puiTransitionContextCount`.  
  
-   Pokud `pTransitionContexts` je hodnotou not null, funkce považuje se za pole struktury délky `puiTransitionContextCount`. Je dán velikost struktury `uiSizeOfContext`, a musí být velikost [simplecontext –](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) nebo `CONTEXT` pro architekturu.  
  
-   `wszTextOut`je napsána v následujícím formátu:  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   Pokud posun v šestnáctkové soustavě 0x0, je zapsán posunutí.  
  
-   Pokud je spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí hodnotu SOS_E_NOMANAGEDCODE.  
  
-   `Flags` Parametru se 0 nebo SOS_STACKTRACE_SHOWADDRESSES zobrazíte EBP a ESP před každou `module!functionname` řádku. Ve výchozím nastavení je 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** SOS_Stacktrace.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
