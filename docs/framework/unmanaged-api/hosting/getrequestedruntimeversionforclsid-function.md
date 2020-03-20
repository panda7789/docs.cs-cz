---
title: GetRequestedRuntimeVersionForCLSID – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178106"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="2e386-102">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="2e386-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="2e386-103">Získá příslušné informace o verzi clr (COMMON Language Runtime) pro třídu se zadanou `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="2e386-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="2e386-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="2e386-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e386-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e386-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e386-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e386-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="2e386-107">[v]  Součást. `CLSID`</span><span class="sxs-lookup"><span data-stu-id="2e386-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="2e386-108">[out]  Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="2e386-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2e386-109">[v]  Velikost, v širokých znaků `pVersion` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e386-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2e386-110">[out] Délka vrácené vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="2e386-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="2e386-111">[v]  Jedna z CLSID_RESOLUTION_FLAGS hodnot.</span><span class="sxs-lookup"><span data-stu-id="2e386-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="2e386-112">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2e386-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="2e386-113">CLSID_RESOLUTION_DEFAULT: (0x0) Určuje, že má být použito výchozí chování interop.</span><span class="sxs-lookup"><span data-stu-id="2e386-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="2e386-114">CLSID_RESOLUTION_REGISTERED: (0x1) Určuje, že registr by měl být prohledán a měl by být použit a použity zásady překrytí.</span><span class="sxs-lookup"><span data-stu-id="2e386-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e386-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e386-115">Return Value</span></span>  
  
|<span data-ttu-id="2e386-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e386-116">HRESULT</span></span>|<span data-ttu-id="2e386-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2e386-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e386-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e386-118">S_OK</span></span>|<span data-ttu-id="2e386-119">Funkce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2e386-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="2e386-120">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="2e386-120">E_INVALIDARG</span></span>|<span data-ttu-id="2e386-121">Jeden z parametrů má neplatný typ nebo formát.</span><span class="sxs-lookup"><span data-stu-id="2e386-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="2e386-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2e386-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2e386-123">Vyrovnávací `pVersion` paměť není dostatečně velká pro uložení celého řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="2e386-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="2e386-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="2e386-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="2e386-125">Neexistuje žádná třída registrovaná `CLSID`s zadanou .</span><span class="sxs-lookup"><span data-stu-id="2e386-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="2e386-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2e386-126">E_POINTER</span></span>|<span data-ttu-id="2e386-127">`dwLength`je null `cchBuffer` nebo je dostatečně velký pro `pVersion` uložení řetězce verze, ale je null.</span><span class="sxs-lookup"><span data-stu-id="2e386-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e386-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e386-128">Requirements</span></span>  
 <span data-ttu-id="2e386-129">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e386-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e386-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e386-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e386-131">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e386-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e386-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e386-132">See also</span></span>

- [<span data-ttu-id="2e386-133">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="2e386-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
