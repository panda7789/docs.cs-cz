---
title: ICLRMetaHost::GetVersionFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd5d2e820bd1d733bb4ab968a89174124bc91357
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962939"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="0edc3-102">ICLRMetaHost::GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="0edc3-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="0edc3-103">Získá původní verzi .NET Framework kompilace sestavení (uloženou v metadatech), která má za následek cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="0edc3-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="0edc3-104">Tato metoda nahrazuje funkci [GetFileVersion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0edc3-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0edc3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0edc3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0edc3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0edc3-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="0edc3-107">pro Úplná cesta k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="0edc3-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="0edc3-108">mimo Verze kompilace .NET Framework uložená v metadatech ve formátu "v*A*. *B* [. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="0edc3-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="0edc3-109">A, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="0edc3-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="0edc3-110">Délka tohoto řetězce je omezená na MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="0edc3-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0edc3-111">Tento výstup se shoduje s názvem adresáře pro .NET Framework verzi, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="0edc3-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="0edc3-112">Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *X*, kde *x* závisí na nainstalovaném čísle sestavení.</span><span class="sxs-lookup"><span data-stu-id="0edc3-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="0edc3-113">Všimněte si, že je vyžadována předpona "v".</span><span class="sxs-lookup"><span data-stu-id="0edc3-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="0edc3-114">[in, out] Velikost `pwzbuffer` , která se má vyhnout přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0edc3-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0edc3-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0edc3-115">Return Value</span></span>  
 <span data-ttu-id="0edc3-116">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="0edc3-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0edc3-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0edc3-117">HRESULT</span></span>|<span data-ttu-id="0edc3-118">Popis</span><span class="sxs-lookup"><span data-stu-id="0edc3-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0edc3-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="0edc3-119">S_OK</span></span>|<span data-ttu-id="0edc3-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0edc3-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="0edc3-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0edc3-121">E_POINTER</span></span>|<span data-ttu-id="0edc3-122">`pwzbuffer`nebo `pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0edc3-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="0edc3-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="0edc3-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="0edc3-124">Vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="0edc3-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0edc3-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0edc3-125">Requirements</span></span>  
 <span data-ttu-id="0edc3-126">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0edc3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0edc3-127">**Hlaviček** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0edc3-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0edc3-128">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0edc3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0edc3-129">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0edc3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edc3-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0edc3-130">See also</span></span>

- [<span data-ttu-id="0edc3-131">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0edc3-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="0edc3-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="0edc3-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
