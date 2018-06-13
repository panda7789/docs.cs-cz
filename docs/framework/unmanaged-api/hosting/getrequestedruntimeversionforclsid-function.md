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
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432856"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="fa757-102">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="fa757-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="fa757-103">Získá odpovídající běžné language runtime (CLR) verze informace pro třídu se zadaným `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="fa757-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="fa757-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa757-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa757-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa757-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa757-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa757-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="fa757-107">[v]  `CLSID` Součásti.</span><span class="sxs-lookup"><span data-stu-id="fa757-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="fa757-108">[out]  Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="fa757-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="fa757-109">[v]  Velikost v široké znaky z `pVersion` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fa757-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="fa757-110">[out] Délka v bajtech vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fa757-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="fa757-111">[v]  Jedna z hodnot CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="fa757-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="fa757-112">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="fa757-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="fa757-113">CLSID_RESOLUTION_DEFAULT: (0x0) určuje výchozí chování spolupráce by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="fa757-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="fa757-114">CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že registru by měl být vyhledávat a kód shim zásad by měla být použita.</span><span class="sxs-lookup"><span data-stu-id="fa757-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa757-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa757-115">Return Value</span></span>  
  
|<span data-ttu-id="fa757-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa757-116">HRESULT</span></span>|<span data-ttu-id="fa757-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fa757-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa757-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa757-118">S_OK</span></span>|<span data-ttu-id="fa757-119">Funkce vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="fa757-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="fa757-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fa757-120">E_INVALIDARG</span></span>|<span data-ttu-id="fa757-121">Jeden z parametrů má neplatný typ nebo formát.</span><span class="sxs-lookup"><span data-stu-id="fa757-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="fa757-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fa757-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fa757-123">`pVersion` Vyrovnávací paměť není dostatečně velký pro uložení řetězec celou verzi.</span><span class="sxs-lookup"><span data-stu-id="fa757-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="fa757-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="fa757-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="fa757-125">Neexistuje žádná třída zaregistrovat se zadaným `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="fa757-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="fa757-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fa757-126">E_POINTER</span></span>|<span data-ttu-id="fa757-127">`dwLength` má hodnotu null, nebo `cchBuffer` je dostatečně velký pro uložení řetězec verze, ale `pVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="fa757-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa757-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa757-128">Requirements</span></span>  
 <span data-ttu-id="fa757-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa757-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa757-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fa757-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fa757-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa757-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa757-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa757-132">See Also</span></span>  
 [<span data-ttu-id="fa757-133">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="fa757-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
