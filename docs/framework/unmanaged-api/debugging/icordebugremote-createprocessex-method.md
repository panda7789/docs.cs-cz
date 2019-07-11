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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744772"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="c4b31-102">ICorDebugRemote::CreateProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b31-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="c4b31-103">Spustí nějaký proces ve vzdáleném počítači v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="c4b31-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4b31-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c4b31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4b31-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="c4b31-106">[in] Ukazatel [icordebugremotetarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c4b31-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="c4b31-107">Slouží k určení vzdáleného počítače, na kterém se spustí proces.</span><span class="sxs-lookup"><span data-stu-id="c4b31-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="c4b31-108">[in] Ukazatel na řetězec zakončený hodnotou null, který určuje modulu je spuštěn proces provést.</span><span class="sxs-lookup"><span data-stu-id="c4b31-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="c4b31-109">Modul provádí v kontextu zabezpečení volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="c4b31-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="c4b31-110">[in] Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který se spustí proces spuštěný.</span><span class="sxs-lookup"><span data-stu-id="c4b31-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="c4b31-111">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="c4b31-112">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="c4b31-113">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="c4b31-114">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="c4b31-115">[in] Ukazatele na blok prostředí nového procesu.</span><span class="sxs-lookup"><span data-stu-id="c4b31-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="c4b31-116">[in] Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k adresáři aktuální proces.</span><span class="sxs-lookup"><span data-stu-id="c4b31-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="c4b31-117">Pokud má parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.</span><span class="sxs-lookup"><span data-stu-id="c4b31-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="c4b31-118">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="c4b31-119">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="c4b31-120">[in] Nepoužitý pro vzdálené ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c4b31-121">[out] Ukazatel na adresu "Icordebugprocess – rozhraní" objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="c4b31-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4b31-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4b31-122">Return Value</span></span>  
 <span data-ttu-id="c4b31-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4b31-123">S_OK</span></span>  
 <span data-ttu-id="c4b31-124">Byl úspěšně spuštěn proces na vzdáleném počítači a vrácené "icordebugprocess – rozhraní" pro ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="c4b31-125">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="c4b31-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c4b31-126">Nelze spustit proces na vzdáleném počítači a vrátit "Icordebugprocess – rozhraní" pro ladění.</span><span class="sxs-lookup"><span data-stu-id="c4b31-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b31-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4b31-127">Remarks</span></span>  
 <span data-ttu-id="c4b31-128">Ladění ve smíšeném režimu není v Silverlightu podporovaný.</span><span class="sxs-lookup"><span data-stu-id="c4b31-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b31-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4b31-129">Requirements</span></span>  
 <span data-ttu-id="c4b31-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b31-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b31-131">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c4b31-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c4b31-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b31-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b31-133">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c4b31-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b31-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4b31-134">See also</span></span>

- [<span data-ttu-id="c4b31-135">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4b31-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="c4b31-136">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4b31-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="c4b31-137">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4b31-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
