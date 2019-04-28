---
title: ICLRDebuggingLibraryProvider::ProvideLibrary – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f5d44b6497e971e6d1ed030c043b91b88c070b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697808"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="44667-102">ICLRDebuggingLibraryProvider::ProvideLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="44667-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>
<span data-ttu-id="44667-103">Získá zprostředkovatele knihovny, rozhraní zpětného volání, které umožňuje knihovnám ladění specifickým pro verzi modulu runtime (CLR) k vyhledání a načtení na požádání.</span><span class="sxs-lookup"><span data-stu-id="44667-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44667-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44667-104">Syntax</span></span>  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44667-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44667-105">Parameters</span></span>  
 `pwszFilename`  
 <span data-ttu-id="44667-106">[in] Název modulu žádá.</span><span class="sxs-lookup"><span data-stu-id="44667-106">[in] The name of the module being requested.</span></span>  
  
 `dwTimestamp`  
 <span data-ttu-id="44667-107">[in] Časové razítko uložené v hlavičce souboru COFF soubory PE.</span><span class="sxs-lookup"><span data-stu-id="44667-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="44667-108">[in] `SizeOfImage` Pole uloženo v hlavičce souboru COFF volitelný soubor PE souborů.</span><span class="sxs-lookup"><span data-stu-id="44667-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>  
  
 `hModule`  
 <span data-ttu-id="44667-109">[out] Popisovač na požadovaný modul.</span><span class="sxs-lookup"><span data-stu-id="44667-109">[out] The handle to the requested module.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44667-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44667-110">Return Value</span></span>  
 <span data-ttu-id="44667-111">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="44667-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44667-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44667-112">HRESULT</span></span>|<span data-ttu-id="44667-113">Popis</span><span class="sxs-lookup"><span data-stu-id="44667-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44667-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="44667-114">S_OK</span></span>|<span data-ttu-id="44667-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="44667-115">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="44667-116">Výjimky</span><span class="sxs-lookup"><span data-stu-id="44667-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44667-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44667-117">Remarks</span></span>  
 <span data-ttu-id="44667-118">`ProvideLibrary` Umožňuje ladicí program poskytuje moduly, které jsou potřeba pro ladění konkrétní soubory CLR, jako je například knihovna mscordbi.dll a souboru mscordacwks.dll.</span><span class="sxs-lookup"><span data-stu-id="44667-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="44667-119">Obslužné rutiny modulu musí zůstat platný až do volání [iclrdebugging::canunloadnow –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) metoda naznačuje, že může být uvolněna, v tomto okamžiku je odpovědností volajícího uvolnit úchyty.</span><span class="sxs-lookup"><span data-stu-id="44667-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>  
  
 <span data-ttu-id="44667-120">Ladicí program může použít všechny dostupné prostředky vyhledejte nebo pořídit modulu ladění.</span><span class="sxs-lookup"><span data-stu-id="44667-120">The debugger may use any available means to locate or procure the debugging module.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44667-121">Tato funkce umožňuje rozhraní API volajícímu zadat moduly, které obsahují spustitelný soubor a potenciálně škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="44667-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="44667-122">Jako bezpečnostní opatření, nepoužívejte, volající `ProvideLibrary` distribuovat veškerý kód, že není natolik, abyste spuštění samotný.</span><span class="sxs-lookup"><span data-stu-id="44667-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>  
>   
>  <span data-ttu-id="44667-123">Pokud je zjištěno závažný bezpečnostní problém již vydané knihovny, jako je například knihovna mscordbi.dll nebo souboru mscordacwks.dll, nejde opravit shimu rozpoznat chybná verze souborů.</span><span class="sxs-lookup"><span data-stu-id="44667-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="44667-124">Překrytí pak můžete vydávat žádosti pro nainstalovanou verzí souborů a odmítnout chybná verze, pokud nejsou zadány žádné požadavku.</span><span class="sxs-lookup"><span data-stu-id="44667-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="44667-125">Tato situace může nastat, pouze v případě, že uživatel má použít pro novou verzi shimu.</span><span class="sxs-lookup"><span data-stu-id="44667-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="44667-126">Verze bez opravy zabezpečení se nadále zranitelné.</span><span class="sxs-lookup"><span data-stu-id="44667-126">Unpatched versions will remain vulnerable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44667-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44667-127">Requirements</span></span>  
 <span data-ttu-id="44667-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44667-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44667-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44667-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44667-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44667-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44667-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44667-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44667-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44667-132">See also</span></span>

- [<span data-ttu-id="44667-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="44667-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="44667-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="44667-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
