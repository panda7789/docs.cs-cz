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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b4ac1a37c2b3506216499ed0c9f8194949b768
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985644"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="62072-102">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="62072-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="62072-103">Získá odpovídající common language runtime (CLR) informace o verzi pro třídu se zadaným `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="62072-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="62072-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62072-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62072-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62072-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62072-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62072-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="62072-107">[in]  `CLSID` Komponenty.</span><span class="sxs-lookup"><span data-stu-id="62072-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="62072-108">[out]  Vyrovnávací paměť, která obsahuje řetězec, číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="62072-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="62072-109">[in]  Velikost v širokých znaků, z `pVersion` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="62072-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="62072-110">[out] Délka v bajtech, vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="62072-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="62072-111">[in]  Jedna z hodnot clsid_resolution_flags –.</span><span class="sxs-lookup"><span data-stu-id="62072-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="62072-112">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="62072-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="62072-113">CLSID_RESOLUTION_DEFAULT: (0x0) určuje, že má být použito výchozí chování spolupráce.</span><span class="sxs-lookup"><span data-stu-id="62072-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="62072-114">CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že registru vyhledávat a překrytí tato zásada použít.</span><span class="sxs-lookup"><span data-stu-id="62072-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62072-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="62072-115">Return Value</span></span>  
  
|<span data-ttu-id="62072-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62072-116">HRESULT</span></span>|<span data-ttu-id="62072-117">Popis</span><span class="sxs-lookup"><span data-stu-id="62072-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62072-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="62072-118">S_OK</span></span>|<span data-ttu-id="62072-119">Funkci bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="62072-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="62072-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="62072-120">E_INVALIDARG</span></span>|<span data-ttu-id="62072-121">Jeden z parametrů má neplatný typ nebo formát.</span><span class="sxs-lookup"><span data-stu-id="62072-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="62072-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="62072-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="62072-123">`pVersion` Vyrovnávací paměť není dostatečně velký pro umístění celého řetězci verze.</span><span class="sxs-lookup"><span data-stu-id="62072-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="62072-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="62072-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="62072-125">Neexistuje žádná třída zaregistrován se zadaným `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="62072-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="62072-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="62072-126">E_POINTER</span></span>|<span data-ttu-id="62072-127">`dwLength` má hodnotu null, nebo `cchBuffer` je dostatečně velký pro uložení řetězce verze, ale `pVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="62072-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62072-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62072-128">Requirements</span></span>  
 <span data-ttu-id="62072-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62072-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62072-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62072-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62072-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62072-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62072-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62072-132">See also</span></span>

- [<span data-ttu-id="62072-133">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="62072-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
