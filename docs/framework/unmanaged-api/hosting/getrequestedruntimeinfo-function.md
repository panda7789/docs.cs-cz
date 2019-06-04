---
title: GetRequestedRuntimeInfo – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21b96d435bdb0265d31972edbd4038d0b8cd8d2b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490339"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="e1090-102">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="e1090-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="e1090-103">Získá informace o common language runtime (CLR) požadovaný aplikací verzi a adresář.</span><span class="sxs-lookup"><span data-stu-id="e1090-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="e1090-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e1090-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1090-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1090-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1090-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1090-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="e1090-107">[in] Název aplikace.</span><span class="sxs-lookup"><span data-stu-id="e1090-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="e1090-108">[in] Řetězec určující číslo verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e1090-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="e1090-109">[in] Název konfiguračního souboru, který je přidružen `pExe`.</span><span class="sxs-lookup"><span data-stu-id="e1090-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="e1090-110">[in] Jeden nebo více následujících [startup_flags –](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="e1090-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="e1090-111">[in] Jeden nebo více následujících [runtime_info_flags –](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="e1090-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="e1090-112">[out] Vyrovnávací paměť, která obsahuje cestu k adresáři modulu runtime po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="e1090-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="e1090-113">[in] Délka vyrovnávací paměti adresáře.</span><span class="sxs-lookup"><span data-stu-id="e1090-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="e1090-114">[out] Ukazatel na délku řetězce cestu adresáře.</span><span class="sxs-lookup"><span data-stu-id="e1090-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="e1090-115">[out] Vyrovnávací paměť, která obsahuje číslo verze modulu runtime po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="e1090-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e1090-116">[in] Délka vyrovnávací paměti pro řetězec verze.</span><span class="sxs-lookup"><span data-stu-id="e1090-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="e1090-117">[out] Ukazatel na délku řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="e1090-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1090-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e1090-118">Return Value</span></span>  
 <span data-ttu-id="e1090-119">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="e1090-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="e1090-120">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="e1090-120">Return code</span></span>|<span data-ttu-id="e1090-121">Popis</span><span class="sxs-lookup"><span data-stu-id="e1090-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e1090-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1090-122">S_OK</span></span>|<span data-ttu-id="e1090-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="e1090-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="e1090-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e1090-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e1090-125">Adresář vyrovnávací paměť není dostatečně velký pro uložení cesta k adresáři.</span><span class="sxs-lookup"><span data-stu-id="e1090-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="e1090-126">- nebo -</span><span class="sxs-lookup"><span data-stu-id="e1090-126">- or -</span></span><br /><br /> <span data-ttu-id="e1090-127">Verze vyrovnávací paměť není dostatečně velký pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="e1090-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1090-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1090-128">Remarks</span></span>  
 <span data-ttu-id="e1090-129">`GetRequestedRuntimeInfo` Metoda vrátí běhových informací o verzi načten do procesu, což není nutně v počítači nainstalovanou nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="e1090-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="e1090-130">V rozhraní .NET Framework verze 2.0, můžete získat informace o nejnovější verze pomocí `GetRequestedRuntimeInfo` metodu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e1090-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="e1090-131">Zadejte `pExe`, `pwszVersion`, a `pConfigurationFile` parametry jako hodnota null.</span><span class="sxs-lookup"><span data-stu-id="e1090-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="e1090-132">Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION v `RUNTIME_INFO_FLAGS` výčty pro `runtimeInfoFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="e1090-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="e1090-133">`GetRequestedRuntimeInfo` Metoda nevrací na nejnovější verzi modulu CLR v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="e1090-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="e1090-134">Existuje konfigurační soubor aplikace, která určuje načtení konkrétní verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e1090-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="e1090-135">Všimněte si, že rozhraní .NET Framework se použít konfigurační soubor i v případě, že zadáte hodnotu null pro `pConfigurationFile` parametru.</span><span class="sxs-lookup"><span data-stu-id="e1090-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="e1090-136">[CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) byla volána metoda zadání starší verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e1090-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="e1090-137">Aplikace, která byla zkompilována pro starší verzi modulu CLR je právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e1090-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="e1090-138">Pro `runtimeInfoFlags` parametr, můžete zadat jenom jednu z konstant architektury `RUNTIME_INFO_FLAGS` výčtu v čase:</span><span class="sxs-lookup"><span data-stu-id="e1090-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="e1090-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="e1090-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="e1090-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="e1090-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="e1090-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="e1090-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1090-142">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1090-142">Requirements</span></span>  
 <span data-ttu-id="e1090-143">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1090-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1090-144">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1090-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1090-145">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1090-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1090-146">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1090-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1090-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1090-147">See also</span></span>

- [<span data-ttu-id="e1090-148">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="e1090-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="e1090-149">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="e1090-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="e1090-150">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="e1090-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
