---
title: ICorDebug::CreateProcess – metoda
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16e45f3bad92914ce8c7fb0044534789a7a28b2e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess – metoda
Spustí se proces a jeho primární vlákno pod kontrolou ladicího programu.  
  
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
 [v] Ukazatel na řetězec ukončené hodnotou null, který určuje modulu provést spuštěného procesem. V modulu se spouštějí v kontextu zabezpečení volajícího procesu.  
  
 `lpCommandLine`  
 [v] Ukazatel na řetězec ukončené hodnotou null, který určuje příkazový řádek, který má být proveden spuštěného procesem. Název aplikace (například "SomeApp.exe") musí být prvním argumentem.  
  
 `lpProcessAttributes`  
 [v] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovače zabezpečení pro proces. Pokud `lpProcessAttributes` je null, proces získá výchozí popisovač zabezpečení.  
  
 `lpThreadAttributes`  
 [v] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovače zabezpečení pro primární vlákna procesu. Pokud `lpThreadAttributes` je null, vlákno získá výchozí popisovač zabezpečení.  
  
 `bInheritHandles`  
 [v] Nastavte na `true` k označení, že každý zděditelné popisovač v procesu volání zdědí procesu spuštěného nebo `false` k označení nejsou zděděny obslužné rutiny pro zpracování. Zděděné obslužných rutin mají stejnou hodnotu a přístupová práva jako původní obslužné rutiny.  
  
 `dwCreationFlags`  
 [v] Bitové kombinace [Win32 proces vytváření příznaky](http://go.microsoft.com/fwlink/?linkid=69981) které řídí chování spuštěného procesu a s prioritou.  
  
 `lpEnvironment`  
 [v] Ukazatel na blok prostředí pro nový proces.  
  
 `lpCurrentDirectory`  
 [v] Ukazatel na řetězec ukončené hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro proces. Pokud tento parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 [v] Ukazatel na Win32 `STARTUPINFOW` struktura, která určuje okno stanice, desktop, standardní obslužné rutiny a vzhled hlavního okna spuštěného procesu.  
  
 `lpProcessInformation`  
 [v] Ukazatel na Win32 `PROCESS_INFORMATION` struktura, která určuje identifikační informace o procesu spuštění.  
  
 `debuggingFlags`  
 [v] Hodnota CorDebugCreateProcessFlags – výčet, který určuje možnosti ladění.  
  
 `ppProcess`  
 [out] Ukazatel na adresu ICorDebugProcess objektu, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Parametry této metody jsou stejné jako Win32 `CreateProcess` metoda.  
  
 Chcete-li povolit nespravované ve smíšeném režimu ladění, nastavte `dwCreationFlags` k DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS. Pokud chcete použít, pouze spravované ladění, nenastavujte tyto příznaky.  
  
 Pokud ladicího programu a proces být ladit (připojené proces) sdílet jediné konzoly, a pokud spolupráce ladění se používá, je možné pro připojené proces zamčeny konzoly a Zastavit Ladění událostí. Ladicí program zablokuje pak všechny pokusy o použití konzoly. Chcete-li se tomuto problému vyhnout, nastavte příznak CREATE_NEW_CONSOLE `dwCreationFlags` parametr.  
  
 Spolupráce se nepodporuje ladění na systémech Windows 9 x a jiný x86 platformách, například platformu IA-64 a na základě AMD64 platformy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
