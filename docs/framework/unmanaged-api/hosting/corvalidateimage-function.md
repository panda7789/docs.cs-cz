---
title: _CorValidateImage – funkce
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101271823f7b7877bb7f007588b6a164233e5b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432374"
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="d0264-102">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="d0264-102">_CorValidateImage Function</span></span>
<span data-ttu-id="d0264-103">Ověří spravovaný modul bitové kopie a po nějaké době načíst upozorní zavaděč operačního systému.</span><span class="sxs-lookup"><span data-stu-id="d0264-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0264-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0264-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0264-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0264-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="d0264-106">[v] Ukazatel na počáteční umístění bitové kopie k ověření jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="d0264-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="d0264-107">Obrázek musí již načten do paměti.</span><span class="sxs-lookup"><span data-stu-id="d0264-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="d0264-108">[v] Název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="d0264-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0264-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0264-109">Return Value</span></span>  
 <span data-ttu-id="d0264-110">Tato funkce vrátí standardní hodnoty `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, a `E_FAIL`, a také následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d0264-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="d0264-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0264-111">Return value</span></span>|<span data-ttu-id="d0264-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d0264-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="d0264-113">Bitovou kopii je neplatný.</span><span class="sxs-lookup"><span data-stu-id="d0264-113">The image is invalid.</span></span> <span data-ttu-id="d0264-114">Tato hodnota má HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="d0264-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="d0264-115">Obrázek je platný.</span><span class="sxs-lookup"><span data-stu-id="d0264-115">The image is valid.</span></span> <span data-ttu-id="d0264-116">Tato hodnota má HRESULT 0x00000000L.</span><span class="sxs-lookup"><span data-stu-id="d0264-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0264-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0264-117">Remarks</span></span>  
 <span data-ttu-id="d0264-118">V systému Windows XP a novějších verzích kontroluje zavaděč operačního systému pro spravované moduly zkoumáním bit COM popisovač Directory společné hlavičky objekt souboru formátu (COFF).</span><span class="sxs-lookup"><span data-stu-id="d0264-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="d0264-119">Sada bit označuje spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="d0264-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="d0264-120">Pokud zavaděč zjistí spravovaný modul, načte MsCorEE.dll a volání `_CorValidateImage`, který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="d0264-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="d0264-121">Potvrdí, že bitová kopie je platný spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="d0264-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="d0264-122">Vstupní bod v common language runtime (CLR) se změní vstupní bod v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="d0264-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="d0264-123">Pro 64bitové verze systému Windows upraví bitovou kopii, která je v paměti pomocí transformace z PE32 na PE32 + formát.</span><span class="sxs-lookup"><span data-stu-id="d0264-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="d0264-124">Vrátí k zavaděč, když jsou načíst spravovaný modul bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d0264-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="d0264-125">Pro spustitelné bitové kopie operačního systému zavaděč pak zavolá [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkce, bez ohledu na to, vstupní bod uvedený v spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d0264-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="d0264-126">Pro knihovny DLL sestavení Image, zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="d0264-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="d0264-127">`_CorExeMain` nebo `_CorDllMain` provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="d0264-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="d0264-128">Inicializuje modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d0264-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="d0264-129">Vyhledá spravovaný vstupní bod z hlavičky sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="d0264-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="d0264-130">Zahájí spuštění.</span><span class="sxs-lookup"><span data-stu-id="d0264-130">Begins execution.</span></span>  
  
 <span data-ttu-id="d0264-131">Zavaděč volání [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) funkce při správě modulu Image jsou odpojen.</span><span class="sxs-lookup"><span data-stu-id="d0264-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="d0264-132">Tato funkce ale neprovede žádnou akci; právě vrátí.</span><span class="sxs-lookup"><span data-stu-id="d0264-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0264-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0264-133">Requirements</span></span>  
 <span data-ttu-id="d0264-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0264-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0264-135">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0264-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0264-136">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0264-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0264-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0264-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0264-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0264-138">See Also</span></span>  
 [<span data-ttu-id="d0264-139">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="d0264-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
