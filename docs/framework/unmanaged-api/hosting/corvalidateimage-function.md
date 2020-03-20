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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178219"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="967ac-102">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="967ac-102">_CorValidateImage Function</span></span>
<span data-ttu-id="967ac-103">Ověří image spravovaného modulu a upozorní zavaděč operačního systému po jejich načtení.</span><span class="sxs-lookup"><span data-stu-id="967ac-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="967ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="967ac-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="967ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="967ac-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="967ac-106">[v] Ukazatel na počáteční umístění bitové kopie k ověření jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="967ac-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="967ac-107">Obraz již musí být načten do paměti.</span><span class="sxs-lookup"><span data-stu-id="967ac-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="967ac-108">[v] Název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="967ac-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="967ac-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="967ac-109">Return Value</span></span>  
 <span data-ttu-id="967ac-110">Tato funkce vrátí `E_INVALIDARG`standardní `E_OUTOFMEMORY` `E_UNEXPECTED`hodnoty `E_FAIL`, , a , stejně jako následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="967ac-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="967ac-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="967ac-111">Return value</span></span>|<span data-ttu-id="967ac-112">Popis</span><span class="sxs-lookup"><span data-stu-id="967ac-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="967ac-113">Obrázek je neplatný.</span><span class="sxs-lookup"><span data-stu-id="967ac-113">The image is invalid.</span></span> <span data-ttu-id="967ac-114">Tato hodnota má HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="967ac-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="967ac-115">Obrázek je platný.</span><span class="sxs-lookup"><span data-stu-id="967ac-115">The image is valid.</span></span> <span data-ttu-id="967ac-116">Tato hodnota má HRESULT 0x00000000L.</span><span class="sxs-lookup"><span data-stu-id="967ac-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="967ac-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="967ac-117">Remarks</span></span>  
 <span data-ttu-id="967ac-118">V systému Windows XP a novějších verzích zavaděč operačního systému kontroluje spravované moduly kontrolou bitu adresáře popisovače COM v hlavičce coff (Common object file format).</span><span class="sxs-lookup"><span data-stu-id="967ac-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="967ac-119">Bit sady označuje spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="967ac-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="967ac-120">Pokud zavaděč detekuje spravovaný modul, načte soubor `_CorValidateImage`MsCorEE.dll a zavolá , který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="967ac-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="967ac-121">Potvrzuje, že bitová kopie je platný spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="967ac-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="967ac-122">Změní vstupní bod v obraze na vstupní bod v zaběhu společného jazyka (CLR).</span><span class="sxs-lookup"><span data-stu-id="967ac-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="967ac-123">U 64bitových verzí systému Windows upravuje bitovou kopii, která je v paměti, transformací z formátu PE32 na formát PE32+.</span><span class="sxs-lookup"><span data-stu-id="967ac-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="967ac-124">Vrátí se do zavaděče při načtení bitové kopie spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="967ac-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="967ac-125">U spustitelných bitových kopií pak zavaděč operačního systému volá [funkci _CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) bez ohledu na vstupní bod zadaný ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="967ac-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="967ac-126">Pro obrazy sestavení DLL zavaděč volá [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkci.</span><span class="sxs-lookup"><span data-stu-id="967ac-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="967ac-127">`_CorExeMain`nebo `_CorDllMain` provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="967ac-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="967ac-128">Inicializuje CLR.</span><span class="sxs-lookup"><span data-stu-id="967ac-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="967ac-129">Vyhledá spravovaný vstupní bod z hlavičky CLR sestavení.</span><span class="sxs-lookup"><span data-stu-id="967ac-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="967ac-130">Začíná poprava.</span><span class="sxs-lookup"><span data-stu-id="967ac-130">Begins execution.</span></span>  
  
 <span data-ttu-id="967ac-131">Zavaděč volá [funkci _CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) při uvolnění bitových kopií spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="967ac-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="967ac-132">Tato funkce však neprovede žádnou akci; to prostě vrátí.</span><span class="sxs-lookup"><span data-stu-id="967ac-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="967ac-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="967ac-133">Requirements</span></span>  
 <span data-ttu-id="967ac-134">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="967ac-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="967ac-135">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="967ac-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="967ac-136">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="967ac-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="967ac-137">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="967ac-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967ac-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="967ac-138">See also</span></span>

- [<span data-ttu-id="967ac-139">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="967ac-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
