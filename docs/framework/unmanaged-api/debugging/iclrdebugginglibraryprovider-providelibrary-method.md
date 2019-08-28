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
ms.openlocfilehash: a1b02bb74a61e64a3ed9875fcf88e018de9f6317
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041433"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a><span data-ttu-id="62a64-102">ICLRDebuggingLibraryProvider::ProvideLibrary – metoda</span><span class="sxs-lookup"><span data-stu-id="62a64-102">ICLRDebuggingLibraryProvider::ProvideLibrary Method</span></span>

<span data-ttu-id="62a64-103">Získá rozhraní zpětného volání zprostředkovatele knihovny, které umožňuje umístění a načtení knihoven ladění pro Common Language Runtime (CLR) pro konkrétní verzi na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="62a64-103">Gets a library provider callback interface that allows common language runtime (CLR) version-specific debugging libraries to be located and loaded on demand.</span></span>

## <a name="syntax"></a><span data-ttu-id="62a64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62a64-104">Syntax</span></span>

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a><span data-ttu-id="62a64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62a64-105">Parameters</span></span>

`pwszFilename` \
<span data-ttu-id="62a64-106">pro Název požadovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="62a64-106">[in] The name of the module being requested.</span></span>

`dwTimestamp` \
<span data-ttu-id="62a64-107">pro Časové razítko data uložené v hlavičce souboru. COFF v hlavičce souborů PE.</span><span class="sxs-lookup"><span data-stu-id="62a64-107">[in] The date time stamp stored in the COFF file header of PE files.</span></span>

`pLibraryProvider` \
<span data-ttu-id="62a64-108">pro `SizeOfImage` Pole uložené v hlavičce volitelného souboru PE souborů.</span><span class="sxs-lookup"><span data-stu-id="62a64-108">[in] The `SizeOfImage` field stored in the COFF optional file header of PE files.</span></span>

`hModule` \
<span data-ttu-id="62a64-109">mimo Popisovač pro požadovaný modul.</span><span class="sxs-lookup"><span data-stu-id="62a64-109">[out] The handle to the requested module.</span></span>

## <a name="return-value"></a><span data-ttu-id="62a64-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62a64-110">Return Value</span></span>

<span data-ttu-id="62a64-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="62a64-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="62a64-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62a64-112">HRESULT</span></span>|<span data-ttu-id="62a64-113">Popis</span><span class="sxs-lookup"><span data-stu-id="62a64-113">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="62a64-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="62a64-114">S_OK</span></span>|<span data-ttu-id="62a64-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="62a64-115">The method completed successfully.</span></span>|

## <a name="exceptions"></a><span data-ttu-id="62a64-116">Výjimky</span><span class="sxs-lookup"><span data-stu-id="62a64-116">Exceptions</span></span>

## <a name="remarks"></a><span data-ttu-id="62a64-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62a64-117">Remarks</span></span>

<span data-ttu-id="62a64-118">`ProvideLibrary`umožňuje ladicímu programu poskytovat moduly, které jsou potřeba pro ladění specifických souborů CLR, jako je mscordbi. dll a Mscordacwks. dll.</span><span class="sxs-lookup"><span data-stu-id="62a64-118">`ProvideLibrary` allows the debugger to provide modules that are needed for debugging specific CLR files such as mscordbi.dll and mscordacwks.dll.</span></span> <span data-ttu-id="62a64-119">Obsluha modulu musí zůstat platná, dokud volání metody [ICLRDebugging:: CanUnloadNow –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) značí, že mohou být uvolněny, v takovém případě je povinností volajícího uvolnit obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="62a64-119">The module handles have to remain valid until a call to the [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) method indicates that they may be freed, at which point it is the caller’s responsibility to free the handles.</span></span>

<span data-ttu-id="62a64-120">Ladicí program může použít všechny dostupné prostředky k vyhledání nebo zpřístupnění modulu ladění.</span><span class="sxs-lookup"><span data-stu-id="62a64-120">The debugger may use any available means to locate or procure the debugging module.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62a64-121">Tato funkce umožňuje volajícímu rozhraní API poskytovat moduly, které obsahují spustitelný soubor a potenciálně škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="62a64-121">This feature allows the API caller to provide modules that contain executable, and possibly malicious, code.</span></span> <span data-ttu-id="62a64-122">Jako bezpečnostní opatření by volající neměl použít `ProvideLibrary` k distribuci kódu, který není ochotn sám spustit.</span><span class="sxs-lookup"><span data-stu-id="62a64-122">As a security precaution, the caller should not use `ProvideLibrary` to distribute any code that it is not willing to execute itself.</span></span>
>
> <span data-ttu-id="62a64-123">Pokud se závažná chyba zabezpečení zjistí v již vydané knihovně, například mscordbi. dll nebo Mscordacwks. dll, překrytí se dá opravit, aby se rozpoznaly chybné verze souborů.</span><span class="sxs-lookup"><span data-stu-id="62a64-123">If a serious security issue is discovered in an already released library, such as mscordbi.dll or mscordacwks.dll, the shim can be patched to recognize the bad versions of the files.</span></span> <span data-ttu-id="62a64-124">Překrytí pak může vydávat požadavky na opravené verze souborů a zamítnout chybné verze, pokud jsou k dispozici v reakci na libovolný požadavek.</span><span class="sxs-lookup"><span data-stu-id="62a64-124">The shim can then issue requests for the patched versions of the files and reject the bad versions if they are provided in response to any request.</span></span> <span data-ttu-id="62a64-125">K tomu může dojít pouze v případě, že uživatel převedl opravu na novou verzi překrytí.</span><span class="sxs-lookup"><span data-stu-id="62a64-125">This can occur only if the user has patched to a new version of the shim.</span></span> <span data-ttu-id="62a64-126">Neopravené verze zůstanou v ohrožení.</span><span class="sxs-lookup"><span data-stu-id="62a64-126">Unpatched versions will remain vulnerable.</span></span>

## <a name="requirements"></a><span data-ttu-id="62a64-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62a64-127">Requirements</span></span>

<span data-ttu-id="62a64-128">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62a64-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="62a64-129">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62a64-129">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="62a64-130">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62a64-130">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="62a64-131">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62a64-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="62a64-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62a64-132">See also</span></span>

- [<span data-ttu-id="62a64-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="62a64-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="62a64-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="62a64-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
