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
ms.openlocfilehash: 40efc256dde13d645d43f50bb574d73b5668919c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703735"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="41cf2-102">ICLRMetaHost::GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="41cf2-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="41cf2-103">Získá původní verzi .NET Framework kompilace sestavení (uloženou v metadatech), která má za následek cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="41cf2-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="41cf2-104">Tato metoda nahrazuje funkci [GetFileVersion –](getfileversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="41cf2-104">This method supersedes the [GetFileVersion](getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41cf2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41cf2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41cf2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="41cf2-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="41cf2-107">pro Úplná cesta k souboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="41cf2-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="41cf2-108">mimo Verze kompilace .NET Framework uložená v metadatech ve formátu "v*A*. *B*[.\* X\*] ".</span><span class="sxs-lookup"><span data-stu-id="41cf2-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="41cf2-109">*A*, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu.</span><span class="sxs-lookup"><span data-stu-id="41cf2-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="41cf2-110">Délka tohoto řetězce je omezená na MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="41cf2-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41cf2-111">Tento výstup se shoduje s názvem adresáře pro .NET Framework verzi, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="41cf2-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="41cf2-112">Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *X*, kde *x* závisí na nainstalovaném čísle sestavení.</span><span class="sxs-lookup"><span data-stu-id="41cf2-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="41cf2-113">Všimněte si, že je vyžadována předpona "v".</span><span class="sxs-lookup"><span data-stu-id="41cf2-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="41cf2-114">[in, out] Velikost, `pwzbuffer` která se má vyhnout přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="41cf2-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41cf2-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="41cf2-115">Return Value</span></span>  
 <span data-ttu-id="41cf2-116">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="41cf2-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="41cf2-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41cf2-117">HRESULT</span></span>|<span data-ttu-id="41cf2-118">Popis</span><span class="sxs-lookup"><span data-stu-id="41cf2-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41cf2-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="41cf2-119">S_OK</span></span>|<span data-ttu-id="41cf2-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="41cf2-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="41cf2-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="41cf2-121">E_POINTER</span></span>|<span data-ttu-id="41cf2-122">`pwzbuffer`nebo `pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="41cf2-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="41cf2-123">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="41cf2-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="41cf2-124">Vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="41cf2-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41cf2-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41cf2-125">Requirements</span></span>  
 <span data-ttu-id="41cf2-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41cf2-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41cf2-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="41cf2-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="41cf2-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41cf2-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41cf2-129">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41cf2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41cf2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="41cf2-130">See also</span></span>

- [<span data-ttu-id="41cf2-131">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41cf2-131">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="41cf2-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="41cf2-132">Hosting</span></span>](index.md)
