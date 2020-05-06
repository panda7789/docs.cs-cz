---
title: ICorDebug::CreateProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: b9ae2b36bff9b4a6c048a8de99fa7d09350b1401
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859706"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess – metoda
Spustí proces a jeho primární vlákno pod ovládacím prvkem ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateProcess (  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpApplicationName`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje modul, který má být spuštěn spuštěným procesem. Modul je spuštěn v kontextu zabezpečení volajícího procesu.  
  
 `lpCommandLine`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který má být spuštěn spuštěným procesem. Název aplikace (například "SomeApp. exe") musí být prvním argumentem.  
  
 `lpProcessAttributes`  
 pro Ukazatel na strukturu Win32 `SECURITY_ATTRIBUTES` , která určuje popisovač zabezpečení pro daný proces. Pokud `lpProcessAttributes` má hodnotu null, proces Získá výchozí popisovač zabezpečení.  
  
 `lpThreadAttributes`  
 pro Ukazatel na strukturu Win32 `SECURITY_ATTRIBUTES` , která určuje popisovač zabezpečení pro primární podproces procesu. Pokud `lpThreadAttributes` má hodnotu null, vlákno získá výchozí popisovač zabezpečení.  
  
 `bInheritHandles`  
 pro Nastavte na `true` k označení toho, že každý dědičný popisovač v volajícím procesu je zděděný spuštěným procesem `false` , nebo pro indikaci, že popisovače nejsou děděny. Zděděné popisovače mají stejnou hodnotu a přístupová práva jako původní popisovače.  
  
 `dwCreationFlags`  
 pro Bitová kombinace [příznaků vytvoření procesu Win32](/windows/win32/procthread/process-creation-flags) , která řídí třídu priority a chování spuštěného procesu.  
  
 `lpEnvironment`  
 pro Ukazatel na blok prostředí pro nový proces.  
  
 `lpCurrentDirectory`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro daný proces. Pokud má tento parametr hodnotu null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 pro Ukazatel na strukturu Win32 `STARTUPINFOW` , která určuje stanici okna, plochu, standardní popisovače a vzhled hlavního okna pro spuštěný proces.  
  
 `lpProcessInformation`  
 pro Ukazatel na strukturu Win32 `PROCESS_INFORMATION` , která určuje identifikační informace o procesu, který má být spuštěn.  
  
 `debuggingFlags`  
 pro Hodnota výčtu CorDebugCreateProcessFlags –, která určuje možnosti ladění.  
  
 `ppProcess`  
 mimo Ukazatel na adresu objektu ICorDebugProcess, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Parametry této metody jsou stejné jako u metody Win32 `CreateProcess` .  
  
 Pokud chcete povolit nespravovaný ladění ve smíšeném režimu `dwCreationFlags` , nastavte na DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Pokud chcete použít pouze spravované ladění, nenastavujte tyto příznaky.  
  
 Pokud se ladicí program a proces, který má být laděn (připojený proces) sdílí s jedinou konzolou, a pokud se používá spolupráce, je možné, že připojený proces bude blokovat zámky konzoly a zastaví se při události ladění. Ladicí program pak bude blokovat všechny pokusy o použití konzoly. Chcete-li se tomuto problému vyhnout, nastavte příznak CREATE_NEW_CONSOLE `dwCreationFlags` v parametru.  
  
 Ladění spolupráce se nepodporuje na platformách, které nejsou založené na platformě IA-64 a platformě AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebug – rozhraní](icordebug-interface.md)
