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
ms.openlocfilehash: a69fb861f7c2671a5c26245aa544ee99bcbdb56b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901016"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="d4fc3-102">ICorDebug::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="d4fc3-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="d4fc3-103">Spustí proces a jeho primární vlákno pod ovládacím prvkem ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4fc3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d4fc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4fc3-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="d4fc3-106">pro Ukazatel na řetězec zakončený hodnotou null, který určuje modul, který má být spuštěn spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="d4fc3-107">Modul je spuštěn v kontextu zabezpečení volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="d4fc3-108">pro Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který má být spuštěn spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="d4fc3-109">Název aplikace (například "SomeApp. exe") musí být prvním argumentem.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="d4fc3-110">pro Ukazatel na strukturu `SECURITY_ATTRIBUTES` Win32, která určuje popisovač zabezpečení pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="d4fc3-111">Pokud je `lpProcessAttributes` null, proces Získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="d4fc3-112">pro Ukazatel na strukturu `SECURITY_ATTRIBUTES` Win32, která určuje popisovač zabezpečení pro primární podproces procesu.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="d4fc3-113">Pokud je `lpThreadAttributes` null, vlákno získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="d4fc3-114">pro Nastavte na `true` pro indikaci, že je každý dědičný popisovač v volajícím procesu zděděný spuštěným procesem, nebo `false` k označení, že popisovače nejsou děděny.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="d4fc3-115">Zděděné popisovače mají stejnou hodnotu a přístupová práva jako původní popisovače.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="d4fc3-116">pro Bitová kombinace [příznaků vytvoření procesu Win32](/windows/win32/procthread/process-creation-flags) , která řídí třídu priority a chování spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-116">[in] A bitwise combination of the [Win32 Process Creation Flags](/windows/win32/procthread/process-creation-flags) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="d4fc3-117">pro Ukazatel na blok prostředí pro nový proces.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="d4fc3-118">pro Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="d4fc3-119">Pokud má tento parametr hodnotu null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="d4fc3-120">pro Ukazatel na strukturu `STARTUPINFOW` Win32, která určuje stanici okna, plochu, standardní popisovače a vzhled hlavního okna pro spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="d4fc3-121">pro Ukazatel na strukturu `PROCESS_INFORMATION` Win32, která určuje identifikační informace o procesu, který se má spustit.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="d4fc3-122">pro Hodnota výčtu CorDebugCreateProcessFlags –, která určuje možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="d4fc3-123">mimo Ukazatel na adresu objektu ICorDebugProcess, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4fc3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4fc3-124">Remarks</span></span>  
 <span data-ttu-id="d4fc3-125">Parametry této metody jsou stejné jako u metody Win32 `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="d4fc3-126">Pokud chcete povolit nespravovaný ladění ve smíšeném režimu, nastavte `dwCreationFlags` &#124; na DEBUG_PROCESS DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="d4fc3-127">Pokud chcete použít pouze spravované ladění, nenastavujte tyto příznaky.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="d4fc3-128">Pokud se ladicí program a proces, který má být laděn (připojený proces) sdílí s jedinou konzolou, a pokud se používá spolupráce, je možné, že připojený proces bude blokovat zámky konzoly a zastaví se při události ladění.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="d4fc3-129">Ladicí program pak bude blokovat všechny pokusy o použití konzoly.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="d4fc3-130">Tomuto problému se vyhnete nastavením příznaku CREATE_NEW_CONSOLE v parametru `dwCreationFlags`.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="d4fc3-131">Ladění spolupráce se nepodporuje na platformách, které nejsou založené na platformě IA-64 a platformě AMD64.</span><span class="sxs-lookup"><span data-stu-id="d4fc3-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4fc3-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4fc3-132">Requirements</span></span>  
 <span data-ttu-id="d4fc3-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4fc3-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4fc3-134">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4fc3-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4fc3-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d4fc3-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4fc3-136">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4fc3-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fc3-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4fc3-137">See also</span></span>

- [<span data-ttu-id="d4fc3-138">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4fc3-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
