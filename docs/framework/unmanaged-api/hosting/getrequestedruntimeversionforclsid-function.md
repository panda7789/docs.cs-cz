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
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617136"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="75170-102">GetRequestedRuntimeVersionForCLSID – funkce</span><span class="sxs-lookup"><span data-stu-id="75170-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="75170-103">Získá příslušné informace o verzi modulu CLR (Common Language Runtime) pro třídu se zadaným parametrem `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="75170-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="75170-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="75170-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75170-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75170-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75170-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="75170-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="75170-107">pro  `CLSID`Komponenty.</span><span class="sxs-lookup"><span data-stu-id="75170-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="75170-108">mimo  Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="75170-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="75170-109">pro  Velikost vyrovnávací paměti v různých znacích `pVersion` .</span><span class="sxs-lookup"><span data-stu-id="75170-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="75170-110">mimo Délka vrácené vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="75170-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="75170-111">pro  Jedna z hodnot CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="75170-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="75170-112">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="75170-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="75170-113">CLSID_RESOLUTION_DEFAULT: (0x0) určuje, že se má použít výchozí chování spolupráce.</span><span class="sxs-lookup"><span data-stu-id="75170-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="75170-114">CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že by měl být registr prohledáván a musí být použita zásada překrytí.</span><span class="sxs-lookup"><span data-stu-id="75170-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75170-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="75170-115">Return Value</span></span>  
  
|<span data-ttu-id="75170-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75170-116">HRESULT</span></span>|<span data-ttu-id="75170-117">Popis</span><span class="sxs-lookup"><span data-stu-id="75170-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75170-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="75170-118">S_OK</span></span>|<span data-ttu-id="75170-119">Funkce byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="75170-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="75170-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="75170-120">E_INVALIDARG</span></span>|<span data-ttu-id="75170-121">Jeden z parametrů má neplatný typ nebo formát.</span><span class="sxs-lookup"><span data-stu-id="75170-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="75170-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="75170-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="75170-123">`pVersion`Vyrovnávací paměť není dostatečně velká pro uložení celého řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="75170-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="75170-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="75170-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="75170-125">Není zaregistrována žádná třída se zadaným parametrem `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="75170-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="75170-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="75170-126">E_POINTER</span></span>|<span data-ttu-id="75170-127">`dwLength`má hodnotu null nebo `cchBuffer` je dostatečně velká pro uložení řetězce verze, ale `pVersion` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="75170-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75170-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75170-128">Requirements</span></span>  
 <span data-ttu-id="75170-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75170-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75170-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="75170-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75170-131">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75170-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75170-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="75170-132">See also</span></span>

- [<span data-ttu-id="75170-133">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="75170-133">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
