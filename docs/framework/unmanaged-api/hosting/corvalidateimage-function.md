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
ms.openlocfilehash: df9cc0cc86237b1ec439a4ec4fa6a75429c416d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111173"
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="da384-102">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="da384-102">_CorValidateImage Function</span></span>
<span data-ttu-id="da384-103">Ověřuje bitové kopie spravovaného modulu a upozorní zavaděč operačního systému po jejich načtení.</span><span class="sxs-lookup"><span data-stu-id="da384-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da384-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da384-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da384-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da384-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="da384-106">[in] Ukazatel na počáteční umístění image se ověřit jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="da384-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="da384-107">Na obrázku musí být již načtena do paměti.</span><span class="sxs-lookup"><span data-stu-id="da384-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="da384-108">[in] Název souboru obrázku.</span><span class="sxs-lookup"><span data-stu-id="da384-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da384-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da384-109">Return Value</span></span>  
 <span data-ttu-id="da384-110">Tato funkce vrací standardní hodnoty `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, a `E_FAIL`, a také následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="da384-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="da384-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da384-111">Return value</span></span>|<span data-ttu-id="da384-112">Popis</span><span class="sxs-lookup"><span data-stu-id="da384-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="da384-113">Na obrázku je neplatný.</span><span class="sxs-lookup"><span data-stu-id="da384-113">The image is invalid.</span></span> <span data-ttu-id="da384-114">Tato hodnota nemá HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="da384-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="da384-115">Na obrázku je platný.</span><span class="sxs-lookup"><span data-stu-id="da384-115">The image is valid.</span></span> <span data-ttu-id="da384-116">Tato hodnota nemá HRESULT 0x00000000L.</span><span class="sxs-lookup"><span data-stu-id="da384-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da384-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da384-117">Remarks</span></span>  
 <span data-ttu-id="da384-118">Ve Windows XP a novějších verzích ověřuje zavaděč operačního systému pro spravované moduly kontrolou bitu COM popisovač adresáře v společné hlavičky objektu file format (COFF).</span><span class="sxs-lookup"><span data-stu-id="da384-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="da384-119">Sada bit označuje spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="da384-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="da384-120">Pokud zavaděč odhalí spravovaný modul, načtení MsCorEE.dll a volání `_CorValidateImage`, který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="da384-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="da384-121">Potvrzuje se tím, že bitová kopie je platný spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="da384-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="da384-122">Změní vstupní bod v bitové kopii na vstupní bod v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="da384-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="da384-123">Pro 64bitové verze systému Windows upraví obrázek, který je v paměti její transformací z formátu PE32 na formát PE32 +.</span><span class="sxs-lookup"><span data-stu-id="da384-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="da384-124">Vrátí zavaděč, když jsou bitové kopie spravovaného modulu načteny.</span><span class="sxs-lookup"><span data-stu-id="da384-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="da384-125">Pro spustitelné bitové kopie na zavaděči operačního systému pak zavolá [Funkce _CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkce bez ohledu na vstupní bod uvedený ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="da384-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="da384-126">Pro bitové kopie sestavení knihovny DLL, volání zavaděče [_cordllmain –](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="da384-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="da384-127">`_CorExeMain` nebo `_CorDllMain` provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="da384-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="da384-128">Inicializuje modul CLR.</span><span class="sxs-lookup"><span data-stu-id="da384-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="da384-129">Vyhledá spravovaný vstupní bod v záhlaví modulu CLR sestavení.</span><span class="sxs-lookup"><span data-stu-id="da384-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="da384-130">Zahájí vykonávání.</span><span class="sxs-lookup"><span data-stu-id="da384-130">Begins execution.</span></span>  
  
 <span data-ttu-id="da384-131">Volání zavaděče [_corimageunloading –](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) fungovat v případě, že spravované bitové kopie modulu jsou uvolněna.</span><span class="sxs-lookup"><span data-stu-id="da384-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="da384-132">Tato funkce ale neprovede žádnou akci; právě vrátí.</span><span class="sxs-lookup"><span data-stu-id="da384-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da384-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da384-133">Requirements</span></span>  
 <span data-ttu-id="da384-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da384-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da384-135">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da384-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da384-136">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da384-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da384-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da384-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da384-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da384-138">See also</span></span>

- [<span data-ttu-id="da384-139">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="da384-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
