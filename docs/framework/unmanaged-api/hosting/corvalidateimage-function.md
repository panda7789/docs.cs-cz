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
ms.openlocfilehash: 426b39aa3d1ada5ae44565a742b70681a7bcf6d3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493432"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="5480d-102">_CorValidateImage – funkce</span><span class="sxs-lookup"><span data-stu-id="5480d-102">_CorValidateImage Function</span></span>
<span data-ttu-id="5480d-103">Ověří bitové kopie spravovaného modulu a upozorní zavaděče operačního systému poté, co byly načteny.</span><span class="sxs-lookup"><span data-stu-id="5480d-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5480d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5480d-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5480d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5480d-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="5480d-106">pro Ukazatel na počáteční umístění obrázku, který se má ověřit jako spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5480d-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="5480d-107">Bitová kopie již musí být načtena do paměti.</span><span class="sxs-lookup"><span data-stu-id="5480d-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="5480d-108">pro Název souboru obrázku</span><span class="sxs-lookup"><span data-stu-id="5480d-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5480d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5480d-109">Return Value</span></span>  
 <span data-ttu-id="5480d-110">Tato funkce vrací standardní hodnoty `E_INVALIDARG` ,, `E_OUTOFMEMORY` `E_UNEXPECTED` a, a `E_FAIL` také následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5480d-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="5480d-111">Vrácená hodnota</span><span class="sxs-lookup"><span data-stu-id="5480d-111">Return value</span></span>|<span data-ttu-id="5480d-112">Description</span><span class="sxs-lookup"><span data-stu-id="5480d-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="5480d-113">Obrázek je neplatný.</span><span class="sxs-lookup"><span data-stu-id="5480d-113">The image is invalid.</span></span> <span data-ttu-id="5480d-114">Tato hodnota má hodnotu HRESULT 0xC000007BL.</span><span class="sxs-lookup"><span data-stu-id="5480d-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="5480d-115">Bitová kopie je platná.</span><span class="sxs-lookup"><span data-stu-id="5480d-115">The image is valid.</span></span> <span data-ttu-id="5480d-116">Tato hodnota má HRESULT 0x00000000.</span><span class="sxs-lookup"><span data-stu-id="5480d-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5480d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5480d-117">Remarks</span></span>  
 <span data-ttu-id="5480d-118">V systému Windows XP a novějších verzích zavaděč operačního systému kontroluje spravované moduly kontrolou adresáře popisovače COM v hlavičce souboru.</span><span class="sxs-lookup"><span data-stu-id="5480d-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="5480d-119">Sada bitů označuje spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="5480d-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="5480d-120">Pokud zavaděč zjistí spravovaný modul, načte MsCorEE. dll a volání `_CorValidateImage` , který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="5480d-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="5480d-121">Potvrdí, že obrázek je platný spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="5480d-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="5480d-122">Změní vstupní bod v obrázku na vstupní bod v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="5480d-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="5480d-123">Pro 64 verze Windows upraví image, která je v paměti, díky transformaci z PE32 na PE32 + Format.</span><span class="sxs-lookup"><span data-stu-id="5480d-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="5480d-124">Vrátí se zavaděč při načtení imagí spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="5480d-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="5480d-125">U spustitelných imagí zavaděč operačního systému pak zavolá funkci [_CorExeMain](corexemain-function.md) bez ohledu na vstupní bod zadaný ve spustitelném souboru.</span><span class="sxs-lookup"><span data-stu-id="5480d-125">For executable images, the operating system loader then calls the [_CorExeMain](corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="5480d-126">Pro Image sestavení DLL volá zavaděč funkci [_CorDllMain](cordllmain-function.md) .</span><span class="sxs-lookup"><span data-stu-id="5480d-126">For DLL assembly images, the loader calls the [_CorDllMain](cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="5480d-127">`_CorExeMain`nebo `_CorDllMain` provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="5480d-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="5480d-128">Inicializuje modul CLR.</span><span class="sxs-lookup"><span data-stu-id="5480d-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="5480d-129">Vyhledá spravovaný vstupní bod ze záhlaví CLR sestavení.</span><span class="sxs-lookup"><span data-stu-id="5480d-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="5480d-130">Zahájí provádění.</span><span class="sxs-lookup"><span data-stu-id="5480d-130">Begins execution.</span></span>  
  
 <span data-ttu-id="5480d-131">Zavaděč volá funkci [_CorImageUnloading](corimageunloading-function.md) , když jsou bitové kopie spravovaného modulu uvolněny.</span><span class="sxs-lookup"><span data-stu-id="5480d-131">The loader calls the [_CorImageUnloading](corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="5480d-132">Tato funkce ale neprovede žádnou akci. pouze vrátí.</span><span class="sxs-lookup"><span data-stu-id="5480d-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5480d-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5480d-133">Requirements</span></span>  
 <span data-ttu-id="5480d-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5480d-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5480d-135">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5480d-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5480d-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5480d-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5480d-137">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5480d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5480d-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5480d-138">See also</span></span>

- [<span data-ttu-id="5480d-139">Globální statické funkce pro metadata</span><span class="sxs-lookup"><span data-stu-id="5480d-139">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
