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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178157"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="ff947-102">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="ff947-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="ff947-103">Získá informace o verzi a adresáři o clr (CLR) jazyka požadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="ff947-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="ff947-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="ff947-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff947-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff947-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ff947-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff947-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="ff947-107">[v] Název aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff947-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="ff947-108">[v] Řetězec určující číslo verze za běhu.</span><span class="sxs-lookup"><span data-stu-id="ff947-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="ff947-109">[v] Název konfiguračního souboru, který je přidružen k programu `pExe`.</span><span class="sxs-lookup"><span data-stu-id="ff947-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="ff947-110">[v] Jedna nebo více [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="ff947-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="ff947-111">[v] Jedna nebo více [hodnot RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="ff947-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="ff947-112">[out] Vyrovnávací paměť, která obsahuje cestu k adresáři do běhu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="ff947-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="ff947-113">[v] Délka vyrovnávací paměti adresáře.</span><span class="sxs-lookup"><span data-stu-id="ff947-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="ff947-114">[out] Ukazatel na délku řetězce cesty k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ff947-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ff947-115">[out] Vyrovnávací paměť, která obsahuje číslo verze za běhu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="ff947-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ff947-116">[v] Délka vyrovnávací paměti řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="ff947-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="ff947-117">[out] Ukazatel na délku řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="ff947-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff947-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff947-118">Return Value</span></span>  
 <span data-ttu-id="ff947-119">Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="ff947-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ff947-120">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="ff947-120">Return code</span></span>|<span data-ttu-id="ff947-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ff947-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ff947-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff947-122">S_OK</span></span>|<span data-ttu-id="ff947-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ff947-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="ff947-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ff947-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ff947-125">Vyrovnávací paměť adresáře není dostatečně velká pro uložení cesty k adresáři.</span><span class="sxs-lookup"><span data-stu-id="ff947-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="ff947-126">- nebo -</span><span class="sxs-lookup"><span data-stu-id="ff947-126">- or -</span></span><br /><br /> <span data-ttu-id="ff947-127">Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="ff947-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff947-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff947-128">Remarks</span></span>  
 <span data-ttu-id="ff947-129">Metoda `GetRequestedRuntimeInfo` vrátí informace za běhu o verzi načtené do procesu, což nemusí být nutně nejnovější verze nainstalovaná v počítači.</span><span class="sxs-lookup"><span data-stu-id="ff947-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="ff947-130">V rozhraní .NET Framework verze 2.0 můžete získat informace o `GetRequestedRuntimeInfo` nejnovější nainstalované verzi pomocí metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ff947-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="ff947-131">Zadejte `pExe` `pwszVersion`parametry `pConfigurationFile` , a parametry jako null.</span><span class="sxs-lookup"><span data-stu-id="ff947-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="ff947-132">Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION `RUNTIME_INFO_FLAGS` ve výčtech `runtimeInfoFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="ff947-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="ff947-133">Metoda `GetRequestedRuntimeInfo` nevrací nejnovější verzi CLR za následujících okolností:</span><span class="sxs-lookup"><span data-stu-id="ff947-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="ff947-134">Existuje konfigurační soubor aplikace, který určuje načtení konkrétní verze CLR.</span><span class="sxs-lookup"><span data-stu-id="ff947-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="ff947-135">Všimněte si, že rozhraní .NET Framework použije konfigurační soubor i v případě, že pro parametr zadáte hodnotu `pConfigurationFile` null.</span><span class="sxs-lookup"><span data-stu-id="ff947-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="ff947-136">Metoda [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) byla volána určující starší verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="ff947-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="ff947-137">Aplikace, která byla zkompilována pro starší verzi CLR, je aktuálně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="ff947-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="ff947-138">Pro `runtimeInfoFlags` parametr můžete zadat pouze jednu konstantu `RUNTIME_INFO_FLAGS` architektury výčtu současně:</span><span class="sxs-lookup"><span data-stu-id="ff947-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="ff947-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="ff947-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="ff947-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="ff947-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="ff947-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="ff947-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff947-142">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff947-142">Requirements</span></span>  
 <span data-ttu-id="ff947-143">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff947-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff947-144">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff947-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff947-145">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff947-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff947-146">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff947-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff947-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff947-147">See also</span></span>

- [<span data-ttu-id="ff947-148">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="ff947-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="ff947-149">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="ff947-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="ff947-150">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ff947-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
