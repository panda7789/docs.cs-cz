---
title: ICorDebugRemote::CreateProcessEx – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
ms.openlocfilehash: cfec84483d387630623f77c176c668171303dd0f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791979"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="f3fd2-102">ICorDebugRemote::CreateProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f3fd2-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="f3fd2-103">Spustí proces na vzdáleném počítači v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3fd2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
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
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3fd2-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="f3fd2-106">pro Ukazatel na [rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd2-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="f3fd2-107">Slouží k určení vzdáleného počítače, na kterém se proces spustí.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="f3fd2-108">pro Ukazatel na řetězec zakončený hodnotou null, který určuje modul, který má být spuštěn spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="f3fd2-109">Modul je spuštěn v kontextu zabezpečení volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="f3fd2-110">pro Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který má být spuštěn spuštěným procesem.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="f3fd2-111">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="f3fd2-112">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="f3fd2-113">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="f3fd2-114">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="f3fd2-115">pro Ukazatel na blok prostředí pro nový proces.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="f3fd2-116">pro Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro daný proces.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="f3fd2-117">Pokud má tento parametr hodnotu null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="f3fd2-118">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="f3fd2-119">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="f3fd2-120">pro Nevyužité pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="f3fd2-121">mimo Ukazatel na adresu objektu rozhraní ICorDebugProcess, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3fd2-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f3fd2-122">Return Value</span></span>  
 <span data-ttu-id="f3fd2-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3fd2-123">S_OK</span></span>  
 <span data-ttu-id="f3fd2-124">Proces byl úspěšně spuštěn na vzdáleném počítači a pro ladění vrátil rozhraní ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="f3fd2-125">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="f3fd2-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f3fd2-126">Nepovedlo se spustit proces na vzdáleném počítači a vrátit rozhraní ICorDebugProcess pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3fd2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3fd2-127">Remarks</span></span>  
 <span data-ttu-id="f3fd2-128">Ladění ve smíšeném režimu není v Silverlightu podporované.</span><span class="sxs-lookup"><span data-stu-id="f3fd2-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fd2-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3fd2-129">Requirements</span></span>  
 <span data-ttu-id="f3fd2-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fd2-131">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="f3fd2-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f3fd2-132">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3fd2-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3fd2-133">**Verze .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="f3fd2-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fd2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3fd2-134">See also</span></span>

- [<span data-ttu-id="f3fd2-135">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3fd2-135">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="f3fd2-136">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3fd2-136">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="f3fd2-137">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f3fd2-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
