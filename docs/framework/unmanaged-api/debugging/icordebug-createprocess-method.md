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
ms.openlocfilehash: 5e9f5af0a79b36f879b75e331d614edfed7476eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509971"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="fbb13-102">ICorDebug::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb13-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="fbb13-103">Spustí proces a jeho primární vlákno pod kontrolu ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fbb13-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbb13-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fbb13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbb13-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="fbb13-106">[in] Ukazatel na řetězec zakončený hodnotou null, který určuje modulu je spuštěn proces provést.</span><span class="sxs-lookup"><span data-stu-id="fbb13-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="fbb13-107">Modul provádí v kontextu zabezpečení volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="fbb13-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="fbb13-108">[in] Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který se spustí proces spuštěný.</span><span class="sxs-lookup"><span data-stu-id="fbb13-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="fbb13-109">Název aplikace (například "SomeApp.exe") musí být prvním argumentem.</span><span class="sxs-lookup"><span data-stu-id="fbb13-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="fbb13-110">[in] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovač zabezpečení pro proces.</span><span class="sxs-lookup"><span data-stu-id="fbb13-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="fbb13-111">Pokud `lpProcessAttributes` je null, proces získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fbb13-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="fbb13-112">[in] Ukazatel na Win32 `SECURITY_ATTRIBUTES` struktura, která určuje popisovač zabezpečení pro primární vlákno tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="fbb13-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="fbb13-113">Pokud `lpThreadAttributes` je null, vlákno získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fbb13-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="fbb13-114">[in] Nastavte na `true` k označení, že každý popisovač odvoditelný v volající proces zdědí spuštěný proces, nebo `false` k označení, že úchyty nedědí.</span><span class="sxs-lookup"><span data-stu-id="fbb13-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="fbb13-115">Zděděné popisovače mají stejnou hodnotu a přístupová práva jako popisovače původní.</span><span class="sxs-lookup"><span data-stu-id="fbb13-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="fbb13-116">[in] Bitová kombinace hodnot [příznaky vytvoření procesu Win32](https://go.microsoft.com/fwlink/?linkid=69981) , které řídí s prioritou a chování spuštěn proces.</span><span class="sxs-lookup"><span data-stu-id="fbb13-116">[in] A bitwise combination of the [Win32 Process Creation Flags](https://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="fbb13-117">[in] Ukazatele na blok prostředí nového procesu.</span><span class="sxs-lookup"><span data-stu-id="fbb13-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="fbb13-118">[in] Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k adresáři aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="fbb13-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="fbb13-119">Pokud má parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.</span><span class="sxs-lookup"><span data-stu-id="fbb13-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="fbb13-120">[in] Ukazatel na Win32 `STARTUPINFOW` struktura, která určuje stanici oken stanici, desktopových, standardní obslužné rutiny a vzhled hlavního okna pro spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="fbb13-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="fbb13-121">[in] Ukazatel na Win32 `PROCESS_INFORMATION` struktura, která určuje identifikační informace o procesu, která se má spustit.</span><span class="sxs-lookup"><span data-stu-id="fbb13-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="fbb13-122">[in] Hodnota cordebugcreateprocessflags – výčet, který určuje možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="fbb13-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="fbb13-123">[out] Ukazatel na adresu ICorDebugProcess objektu, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="fbb13-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb13-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbb13-124">Remarks</span></span>  
 <span data-ttu-id="fbb13-125">Parametry této metody jsou stejné jako u Win32 `CreateProcess` metody.</span><span class="sxs-lookup"><span data-stu-id="fbb13-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="fbb13-126">Chcete-li povolit nespravované ladění ve smíšeném režimu, nastavte `dwCreationFlags` k DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="fbb13-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="fbb13-127">Pokud chcete použít, pouze spravovaného ladění, nenastavujte tyto příznaky.</span><span class="sxs-lookup"><span data-stu-id="fbb13-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="fbb13-128">Pokud ladicí program a proces se ladí (připojený proces) sdílet pomocí jediné konzole, a pokud definiční ladění se používá, je možné pro připojený proces pro uložení konzoly zámky zastavení při ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="fbb13-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="fbb13-129">Ladicí program bude blokovat pak všechny pokusy o použití konzoly.</span><span class="sxs-lookup"><span data-stu-id="fbb13-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="fbb13-130">Chcete-li tomuto problému vyhnout, nastavte příznak CREATE_NEW_CONSOLE `dwCreationFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="fbb13-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="fbb13-131">Definiční ladění není podporováno na platformách Win9x a jiných x86, například platformu IA-64 a AMD64 podle platformy.</span><span class="sxs-lookup"><span data-stu-id="fbb13-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb13-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbb13-132">Requirements</span></span>  
 <span data-ttu-id="fbb13-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb13-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb13-134">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbb13-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbb13-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbb13-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb13-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb13-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb13-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbb13-137">See also</span></span>
- [<span data-ttu-id="fbb13-138">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb13-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
