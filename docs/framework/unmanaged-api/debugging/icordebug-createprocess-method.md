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
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="d0343-102">ICorDebug::CreateProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="d0343-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="d0343-103">Spustí proces a jeho primární vlákno pod ovládacím prvkem ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="d0343-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0343-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d0343-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0343-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="d0343-106">pro Ukazatel na řetězec zakončený hodnotou null, který určuje modul, který má být spuštěn spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="d0343-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="d0343-107">Modul je spuštěn v kontextu zabezpečení volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="d0343-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="d0343-108">pro Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který má být spuštěn spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="d0343-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="d0343-109">Název aplikace (například "SomeApp. exe") musí být prvním argumentem.</span><span class="sxs-lookup"><span data-stu-id="d0343-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="d0343-110">pro Ukazatel na strukturu `SECURITY_ATTRIBUTES` Win32, která určuje popisovač zabezpečení pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="d0343-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="d0343-111">Pokud je `lpProcessAttributes` null, proces Získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d0343-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="d0343-112">pro Ukazatel na strukturu `SECURITY_ATTRIBUTES` Win32, která určuje popisovač zabezpečení pro primární podproces procesu.</span><span class="sxs-lookup"><span data-stu-id="d0343-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="d0343-113">Pokud je `lpThreadAttributes` null, vlákno získá výchozí popisovač zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d0343-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="d0343-114">pro Nastavte na `true` pro indikaci, že je každý dědičný popisovač v volajícím procesu zděděný spuštěným procesem, nebo `false` k označení, že popisovače nejsou děděny.</span><span class="sxs-lookup"><span data-stu-id="d0343-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="d0343-115">Zděděné popisovače mají stejnou hodnotu a přístupová práva jako původní popisovače.</span><span class="sxs-lookup"><span data-stu-id="d0343-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="d0343-116">pro Bitová kombinace [příznaků vytvoření procesu Win32](https://go.microsoft.com/fwlink/?linkid=69981) , která řídí třídu priority a chování spuštěného procesu.</span><span class="sxs-lookup"><span data-stu-id="d0343-116">[in] A bitwise combination of the [Win32 Process Creation Flags](https://go.microsoft.com/fwlink/?linkid=69981) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="d0343-117">pro Ukazatel na blok prostředí pro nový proces.</span><span class="sxs-lookup"><span data-stu-id="d0343-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="d0343-118">pro Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="d0343-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="d0343-119">Pokud má tento parametr hodnotu null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.</span><span class="sxs-lookup"><span data-stu-id="d0343-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="d0343-120">pro Ukazatel na strukturu `STARTUPINFOW` Win32, která určuje stanici okna, plochu, standardní popisovače a vzhled hlavního okna pro spuštěný proces.</span><span class="sxs-lookup"><span data-stu-id="d0343-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="d0343-121">pro Ukazatel na strukturu `PROCESS_INFORMATION` Win32, která určuje identifikační informace o procesu, který se má spustit.</span><span class="sxs-lookup"><span data-stu-id="d0343-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="d0343-122">pro Hodnota výčtu CorDebugCreateProcessFlags –, která určuje možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="d0343-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="d0343-123">mimo Ukazatel na adresu objektu ICorDebugProcess, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="d0343-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0343-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0343-124">Remarks</span></span>  
 <span data-ttu-id="d0343-125">Parametry této metody jsou stejné jako u metody Win32 `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="d0343-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="d0343-126">Pokud chcete povolit nespravovaný ladění ve smíšeném režimu, nastavte `dwCreationFlags` &#124; na DEBUG_PROCESS DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="d0343-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="d0343-127">Pokud chcete použít pouze spravované ladění, nenastavujte tyto příznaky.</span><span class="sxs-lookup"><span data-stu-id="d0343-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="d0343-128">Pokud se ladicí program a proces, který má být laděn (připojený proces) sdílí s jedinou konzolou, a pokud se používá spolupráce, je možné, že připojený proces bude blokovat zámky konzoly a zastaví se při události ladění.</span><span class="sxs-lookup"><span data-stu-id="d0343-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="d0343-129">Ladicí program pak bude blokovat všechny pokusy o použití konzoly.</span><span class="sxs-lookup"><span data-stu-id="d0343-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="d0343-130">Tomuto problému se vyhnete nastavením příznaku CREATE_NEW_CONSOLE v parametru `dwCreationFlags`.</span><span class="sxs-lookup"><span data-stu-id="d0343-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="d0343-131">Ladění spolupráce se nepodporuje na platformách, které nejsou založené na platformě IA-64 a platformě AMD64.</span><span class="sxs-lookup"><span data-stu-id="d0343-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0343-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0343-132">Requirements</span></span>  
 <span data-ttu-id="d0343-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0343-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0343-134">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0343-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0343-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d0343-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0343-136">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0343-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0343-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0343-137">See also</span></span>

- [<span data-ttu-id="d0343-138">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0343-138">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
