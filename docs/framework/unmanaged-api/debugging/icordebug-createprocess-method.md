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
ms.openlocfilehash: 8812a98b0f28dd1336903dc34682f638a291f53b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110998"
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
 pro Ukazatel na strukturu `SECURITY_ATTRIBUTES` Win32, která určuje popisovač zabezpečení pro daný proces. Pokud je `lpProcessAttributes` null, proces Získá výchozí popisovač zabezpečení.  
  
 `lpThreadAttributes`  
 pro Ukazatel na strukturu `SECURITY_ATTRIBUTES` Win32, která určuje popisovač zabezpečení pro primární podproces procesu. Pokud je `lpThreadAttributes` null, vlákno získá výchozí popisovač zabezpečení.  
  
 `bInheritHandles`  
 pro Nastavte na `true` pro indikaci, že je každý dědičný popisovač v volajícím procesu zděděný spuštěným procesem, nebo `false` k označení, že popisovače nejsou děděny. Zděděné popisovače mají stejnou hodnotu a přístupová práva jako původní popisovače.  
  
 `dwCreationFlags`  
 pro Bitová kombinace [příznaků vytvoření procesu Win32](https://go.microsoft.com/fwlink/?linkid=69981) , která řídí třídu priority a chování spuštěného procesu.  
  
 `lpEnvironment`  
 pro Ukazatel na blok prostředí pro nový proces.  
  
 `lpCurrentDirectory`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro daný proces. Pokud má tento parametr hodnotu null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 pro Ukazatel na strukturu `STARTUPINFOW` Win32, která určuje stanici okna, plochu, standardní popisovače a vzhled hlavního okna pro spuštěný proces.  
  
 `lpProcessInformation`  
 pro Ukazatel na strukturu `PROCESS_INFORMATION` Win32, která určuje identifikační informace o procesu, který se má spustit.  
  
 `debuggingFlags`  
 pro Hodnota výčtu CorDebugCreateProcessFlags –, která určuje možnosti ladění.  
  
 `ppProcess`  
 mimo Ukazatel na adresu objektu ICorDebugProcess, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Parametry této metody jsou stejné jako u metody Win32 `CreateProcess`.  
  
 Pokud chcete povolit nespravovaný ladění ve smíšeném režimu, nastavte `dwCreationFlags` &#124; na DEBUG_PROCESS DEBUG_ONLY_THIS_PROCESS. Pokud chcete použít pouze spravované ladění, nenastavujte tyto příznaky.  
  
 Pokud se ladicí program a proces, který má být laděn (připojený proces) sdílí s jedinou konzolou, a pokud se používá spolupráce, je možné, že připojený proces bude blokovat zámky konzoly a zastaví se při události ladění. Ladicí program pak bude blokovat všechny pokusy o použití konzoly. Tomuto problému se vyhnete nastavením příznaku CREATE_NEW_CONSOLE v parametru `dwCreationFlags`.  
  
 Ladění spolupráce se nepodporuje na platformách, které nejsou založené na platformě IA-64 a platformě AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
