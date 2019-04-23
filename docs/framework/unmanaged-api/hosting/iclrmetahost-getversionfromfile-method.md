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
ms.openlocfilehash: 2a6c7fd48269a3e8291a548b3e13efe5c8e70652
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150810"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="d2f7d-102">ICLRMetaHost::GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d2f7d-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="d2f7d-103">Získá sestavení původní verzi rozhraní .NET Framework kompilace (uložené v metadatech) zadané cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="d2f7d-104">Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f7d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2f7d-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2f7d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2f7d-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="d2f7d-107">[in] Cesta k souboru dokončení sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="d2f7d-108">[out] Kompilace verzi rozhraní .NET Framework uložena v metadatech ve formátu "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="d2f7d-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="d2f7d-109">*A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="d2f7d-110">Délka tohoto řetězce je omezená na MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2f7d-111">Tento výstup odpovídá názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="d2f7d-112">Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na číslo sestavení nainstalována.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="d2f7d-113">Mějte na paměti, že předpona "v" je povinný.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="d2f7d-114">[out v] Velikost `pwzbuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2f7d-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2f7d-115">Return Value</span></span>  
 <span data-ttu-id="d2f7d-116">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d2f7d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2f7d-117">HRESULT</span></span>|<span data-ttu-id="d2f7d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d2f7d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2f7d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2f7d-119">S_OK</span></span>|<span data-ttu-id="d2f7d-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="d2f7d-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d2f7d-121">E_POINTER</span></span>|<span data-ttu-id="d2f7d-122">`pwzbuffer` nebo `pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="d2f7d-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="d2f7d-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="d2f7d-124">Vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="d2f7d-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2f7d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2f7d-125">Requirements</span></span>  
 <span data-ttu-id="d2f7d-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f7d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f7d-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d2f7d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d2f7d-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2f7d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2f7d-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f7d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f7d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2f7d-130">See also</span></span>

- [<span data-ttu-id="d2f7d-131">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2f7d-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="d2f7d-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="d2f7d-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
