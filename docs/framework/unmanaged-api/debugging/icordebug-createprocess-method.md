---
title: "ICorDebug::CreateProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a05bb8d8486f5ae12910d51e3717c4c91ef09cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="8f05b-102">ICorDebug::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="8f05b-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="8f05b-103">Spustí se proces a jeho primární vlákno pod kontrolou ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="8f05b-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f05b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f05b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8f05b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f05b-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="8f05b-106">[v] Ukazatel na řetězec ukončené hodnotou null, který určuje modulu provést spuštěného procesem.</span><span class="sxs-lookup"><span data-stu-id="8f05b-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="8f05b-107">V modulu se spouštějí v kontextu zabezpečení volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="8f05b-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="8f05b-108">[v] Ukazatel na řetězec ukončené hodnotou null, který určuje příkazový řádek, který má být proveden spuštěného procesem.</span><span class="sxs-lookup"><span data-stu-id="8f05b-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="8f05b-109">Název aplikace (například "SomeApp.exe") musí být prvním argumentem.</span><span class="sxs-lookup"><span data-stu-id="8f05b-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="8f05b-110">[v] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovače zabezpečení pro proces.</span><span class="sxs-lookup"><span data-stu-id="8f05b-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="8f05b-111">Pokud `lpProcessAttributes` je null, proces získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8f05b-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="8f05b-112">[v] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovače zabezpečení pro primární vlákna procesu.</span><span class="sxs-lookup"><span data-stu-id="8f05b-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="8f05b-113">Pokud `lpThreadAttributes` je null, vlákno získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8f05b-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="8f05b-114">[v] Nastavte na `true` k označení, že každý zděditelné popisovač v procesu volání zdědí procesu spuštěného nebo `false` k označení nejsou zděděny obslužné rutiny pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="8f05b-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="8f05b-115">Zděděné obslužných rutin mají stejnou hodnotu a přístupová práva jako původní obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="8f05b-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="8f05b-116">[v] Bitové kombinace [Win32 proces vytváření příznaky](http://go.microsoft.com/fwlink/?linkid=69981) které řídí chování spuštěného procesu a s prioritou.</span><span class="sxs-lookup"><span data-stu-id="8f05b-116">[in] A bitwise combination of the [Win32 Process Creation Flags](http://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="8f05b-117">[v] Ukazatel na blok prostředí pro nový proces.</span><span class="sxs-lookup"><span data-stu-id="8f05b-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="8f05b-118">[v] Ukazatel na řetězec ukončené hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro proces.</span><span class="sxs-lookup"><span data-stu-id="8f05b-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="8f05b-119">Pokud tento parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.</span><span class="sxs-lookup"><span data-stu-id="8f05b-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="8f05b-120">[v] Ukazatel na Win32 `STARTUPINFOW` struktura, která určuje okno stanice, desktop, standardní obslužné rutiny a vzhled hlavního okna spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="8f05b-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="8f05b-121">[v] Ukazatel na Win32 `PROCESS_INFORMATION` struktura, která určuje identifikační informace o procesu spuštění.</span><span class="sxs-lookup"><span data-stu-id="8f05b-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="8f05b-122">[v] Hodnota CorDebugCreateProcessFlags – výčet, který určuje možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="8f05b-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="8f05b-123">[out] Ukazatel na adresu ICorDebugProcess objektu, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="8f05b-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f05b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f05b-124">Remarks</span></span>  
 <span data-ttu-id="8f05b-125">Parametry této metody jsou stejné jako Win32 `CreateProcess` metoda.</span><span class="sxs-lookup"><span data-stu-id="8f05b-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="8f05b-126">Chcete-li povolit nespravované ve smíšeném režimu ladění, nastavte `dwCreationFlags` na DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="8f05b-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="8f05b-127">Pokud chcete použít, pouze spravované ladění, nenastavujte tyto příznaky.</span><span class="sxs-lookup"><span data-stu-id="8f05b-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="8f05b-128">Pokud ladicího programu a proces být ladit (připojené proces) sdílet jediné konzoly, a pokud spolupráce ladění se používá, je možné pro připojené proces zamčeny konzoly a Zastavit Ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="8f05b-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="8f05b-129">Ladicí program zablokuje pak všechny pokusy o použití konzoly.</span><span class="sxs-lookup"><span data-stu-id="8f05b-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="8f05b-130">Chcete-li se tomuto problému vyhnout, nastavte příznak CREATE_NEW_CONSOLE `dwCreationFlags` parametr.</span><span class="sxs-lookup"><span data-stu-id="8f05b-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="8f05b-131">Spolupráce se nepodporuje ladění na systémech Windows 9 x a jiný x86 platformách, například platformu IA-64 a na základě AMD64 platformy.</span><span class="sxs-lookup"><span data-stu-id="8f05b-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f05b-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f05b-132">Requirements</span></span>  
 <span data-ttu-id="8f05b-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f05b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f05b-134">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f05b-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f05b-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f05b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f05b-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f05b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f05b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f05b-137">See Also</span></span>  
 [<span data-ttu-id="8f05b-138">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f05b-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
