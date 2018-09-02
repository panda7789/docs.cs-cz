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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfda61706af3e1043d271c0aa74264bd99a4076c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386588"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess – metoda
Spustí proces a jeho primární vlákno pod kontrolu ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `lpApplicationName`  
 [in] Ukazatel na řetězec zakončený hodnotou null, který určuje modulu je spuštěn proces provést. Modul provádí v kontextu zabezpečení volajícího procesu.  
  
 `lpCommandLine`  
 [in] Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který se spustí proces spuštěný. Název aplikace (například "SomeApp.exe") musí být prvním argumentem.  
  
 `lpProcessAttributes`  
 [in] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovač zabezpečení pro proces. Pokud `lpProcessAttributes` je null, proces získá výchozí popisovač zabezpečení.  
  
 `lpThreadAttributes`  
 [in] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovač zabezpečení pro primární vlákno tohoto procesu. Pokud `lpThreadAttributes` je null, vlákno získá výchozí popisovač zabezpečení.  
  
 `bInheritHandles`  
 [in] Nastavte na `true` k označení, že každý popisovač odvoditelný v volající proces zdědí spuštěný proces, nebo `false` k označení, že úchyty nedědí. Zděděné popisovače mají stejnou hodnotu a přístupová práva jako popisovače původní.  
  
 `dwCreationFlags`  
 [in] Bitová kombinace hodnot [příznaky vytvoření procesu Win32](https://go.microsoft.com/fwlink/?linkid=69981) , které řídí s prioritou a chování spuštěn proces.  
  
 `lpEnvironment`  
 [in] Ukazatele na blok prostředí nového procesu.  
  
 `lpCurrentDirectory`  
 [in] Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k adresáři aktuální proces. Pokud má parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 [in] Ukazatel na Win32 `STARTUPINFOW` struktura, která určuje stanici oken stanici, desktopových, standardní obslužné rutiny a vzhled hlavního okna pro spuštěný proces.  
  
 `lpProcessInformation`  
 [in] Ukazatel na Win32 `PROCESS_INFORMATION` struktura, která určuje identifikační informace o procesu, která se má spustit.  
  
 `debuggingFlags`  
 [in] Hodnota cordebugcreateprocessflags – výčet, který určuje možnosti ladění.  
  
 `ppProcess`  
 [out] Ukazatel na adresu ICorDebugProcess objektu, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Parametry této metody jsou stejné jako u Win32 `CreateProcess` metody.  
  
 Chcete-li povolit nespravované ladění ve smíšeném režimu, nastavte `dwCreationFlags` k DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Pokud chcete použít, pouze spravovaného ladění, nenastavujte tyto příznaky.  
  
 Pokud ladicí program a proces se ladí (připojený proces) sdílet pomocí jediné konzole, a pokud definiční ladění se používá, je možné pro připojený proces pro uložení konzoly zámky zastavení při ladění událostí. Ladicí program bude blokovat pak všechny pokusy o použití konzoly. Chcete-li tomuto problému vyhnout, nastavte příznak CREATE_NEW_CONSOLE `dwCreationFlags` parametru.  
  
 Definiční ladění není podporováno na platformách Win9x a jiných x86, například platformu IA-64 a AMD64 podle platformy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
