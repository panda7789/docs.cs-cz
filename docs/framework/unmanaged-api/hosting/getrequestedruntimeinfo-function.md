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
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617175"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="38e47-102">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="38e47-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="38e47-103">Získá informace o verzi a adresáři modulu CLR (Common Language Runtime), který požaduje aplikace.</span><span class="sxs-lookup"><span data-stu-id="38e47-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="38e47-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="38e47-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e47-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e47-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="38e47-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38e47-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="38e47-107">pro Název aplikace</span><span class="sxs-lookup"><span data-stu-id="38e47-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="38e47-108">pro Řetězec určující číslo verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="38e47-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="38e47-109">pro Název konfiguračního souboru, ke kterému je přidružen `pExe` .</span><span class="sxs-lookup"><span data-stu-id="38e47-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="38e47-110">pro Jedna nebo více hodnot [STARTUP_FLAGS](startup-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="38e47-110">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="38e47-111">pro Jedna nebo více hodnot [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="38e47-111">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="38e47-112">mimo Vyrovnávací paměť, která obsahuje cestu k adresáři modulu runtime po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="38e47-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="38e47-113">pro Délka vyrovnávací paměti adresáře.</span><span class="sxs-lookup"><span data-stu-id="38e47-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="38e47-114">mimo Ukazatel na délku řetězce cesty k adresáři.</span><span class="sxs-lookup"><span data-stu-id="38e47-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="38e47-115">mimo Vyrovnávací paměť obsahující číslo verze modulu runtime po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="38e47-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="38e47-116">pro Délka vyrovnávací paměti pro řetězec verze.</span><span class="sxs-lookup"><span data-stu-id="38e47-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="38e47-117">mimo Ukazatel na délku řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="38e47-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38e47-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38e47-118">Return Value</span></span>  
 <span data-ttu-id="38e47-119">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="38e47-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="38e47-120">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="38e47-120">Return code</span></span>|<span data-ttu-id="38e47-121">Popis</span><span class="sxs-lookup"><span data-stu-id="38e47-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="38e47-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="38e47-122">S_OK</span></span>|<span data-ttu-id="38e47-123">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="38e47-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="38e47-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="38e47-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="38e47-125">Vyrovnávací paměť adresáře není dostatečně velká pro uložení cesty k adresáři.</span><span class="sxs-lookup"><span data-stu-id="38e47-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="38e47-126">- nebo -</span><span class="sxs-lookup"><span data-stu-id="38e47-126">- or -</span></span><br /><br /> <span data-ttu-id="38e47-127">Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="38e47-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e47-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38e47-128">Remarks</span></span>  
 <span data-ttu-id="38e47-129">`GetRequestedRuntimeInfo`Metoda vrátí běhové informace o verzi načtené do procesu, což není nutně nejnovější verze nainstalovaná v počítači.</span><span class="sxs-lookup"><span data-stu-id="38e47-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="38e47-130">V .NET Framework verze 2,0 můžete získat informace o nejnovější nainstalované verzi pomocí `GetRequestedRuntimeInfo` metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="38e47-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="38e47-131">Zadejte `pExe` parametry, `pwszVersion` a `pConfigurationFile` jako hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="38e47-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="38e47-132">Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION v `RUNTIME_INFO_FLAGS` výčtech pro `runtimeInfoFlags` parametr.</span><span class="sxs-lookup"><span data-stu-id="38e47-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="38e47-133">`GetRequestedRuntimeInfo`Metoda nevrátí nejnovější verzi CLR v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="38e47-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="38e47-134">Existuje konfigurační soubor aplikace, který určuje načtení konkrétní verze CLR.</span><span class="sxs-lookup"><span data-stu-id="38e47-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="38e47-135">Všimněte si, že .NET Framework bude používat konfigurační soubor i v případě, že pro parametr zadáte hodnotu null `pConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="38e47-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="38e47-136">Metoda [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) byla volána pro zadání dřívější verze CLR.</span><span class="sxs-lookup"><span data-stu-id="38e47-136">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="38e47-137">Aplikace, která byla zkompilována pro starší verzi CLR, je aktuálně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="38e47-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="38e47-138">Pro `runtimeInfoFlags` parametr můžete zadat pouze jednu z konstant architektury `RUNTIME_INFO_FLAGS` výčtu v daném čase:</span><span class="sxs-lookup"><span data-stu-id="38e47-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="38e47-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="38e47-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="38e47-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="38e47-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="38e47-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="38e47-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e47-142">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38e47-142">Requirements</span></span>  
 <span data-ttu-id="38e47-143">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e47-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e47-144">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38e47-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38e47-145">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38e47-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38e47-146">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e47-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e47-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="38e47-147">See also</span></span>

- [<span data-ttu-id="38e47-148">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="38e47-148">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="38e47-149">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="38e47-149">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="38e47-150">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="38e47-150">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
