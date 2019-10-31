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
ms.openlocfilehash: ce0c6307defd93dcf63ac4e9051fc798041475f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127057"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="ec28c-102">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="ec28c-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="ec28c-103">Získá příslušné informace o verzi modulu CLR (Common Language Runtime) pro třídu se zadaným `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="ec28c-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="ec28c-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ec28c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec28c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec28c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec28c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec28c-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="ec28c-107">pro  `CLSID` součásti.</span><span class="sxs-lookup"><span data-stu-id="ec28c-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ec28c-108">mimo  Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="ec28c-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ec28c-109">pro  Velikost `pVersion` vyrovnávací paměti v různých znacích.</span><span class="sxs-lookup"><span data-stu-id="ec28c-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ec28c-110">mimo Délka vrácené vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ec28c-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="ec28c-111">pro  Jedna z hodnot CLSID_RESOLUTION_FLAGS</span><span class="sxs-lookup"><span data-stu-id="ec28c-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="ec28c-112">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="ec28c-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="ec28c-113">CLSID_RESOLUTION_DEFAULT: (0x0) určuje, že se má použít výchozí chování spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec28c-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="ec28c-114">CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že by měl být použit registr a měla by být použita zásada překrytí.</span><span class="sxs-lookup"><span data-stu-id="ec28c-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec28c-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ec28c-115">Return Value</span></span>  
  
|<span data-ttu-id="ec28c-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec28c-116">HRESULT</span></span>|<span data-ttu-id="ec28c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ec28c-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec28c-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec28c-118">S_OK</span></span>|<span data-ttu-id="ec28c-119">Funkce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ec28c-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="ec28c-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ec28c-120">E_INVALIDARG</span></span>|<span data-ttu-id="ec28c-121">Jeden z parametrů má neplatný typ nebo formát.</span><span class="sxs-lookup"><span data-stu-id="ec28c-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="ec28c-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ec28c-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ec28c-123">Vyrovnávací paměť `pVersion` není dostatečně velká pro uložení celého řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="ec28c-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="ec28c-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="ec28c-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="ec28c-125">Není zaregistrována žádná třída se zadaným `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="ec28c-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="ec28c-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ec28c-126">E_POINTER</span></span>|<span data-ttu-id="ec28c-127">`dwLength` má hodnotu null nebo je `cchBuffer` dostatečně velká pro uložení řetězce verze, ale `pVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ec28c-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec28c-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec28c-128">Requirements</span></span>  
 <span data-ttu-id="ec28c-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec28c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec28c-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec28c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec28c-131">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec28c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec28c-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec28c-132">See also</span></span>

- [<span data-ttu-id="ec28c-133">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ec28c-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
