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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61919409"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="7559a-102">ICLRMetaHost::GetVersionFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="7559a-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="7559a-103">Získá sestavení původní verzi rozhraní .NET Framework kompilace (uložené v metadatech) zadané cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="7559a-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="7559a-104">Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="7559a-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7559a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7559a-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7559a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7559a-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="7559a-107">[in] Cesta k souboru dokončení sestavení.</span><span class="sxs-lookup"><span data-stu-id="7559a-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="7559a-108">[out] Kompilace verzi rozhraní .NET Framework uložena v metadatech ve formátu "v*A*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="7559a-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="7559a-109">*A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="7559a-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="7559a-110">Délka tohoto řetězce je omezená na MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="7559a-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7559a-111">Tento výstup odpovídá názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="7559a-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="7559a-112">Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na číslo sestavení nainstalována.</span><span class="sxs-lookup"><span data-stu-id="7559a-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="7559a-113">Mějte na paměti, že předpona "v" je povinný.</span><span class="sxs-lookup"><span data-stu-id="7559a-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="7559a-114">[out v] Velikost `pwzbuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7559a-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7559a-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7559a-115">Return Value</span></span>  
 <span data-ttu-id="7559a-116">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="7559a-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7559a-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7559a-117">HRESULT</span></span>|<span data-ttu-id="7559a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7559a-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7559a-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="7559a-119">S_OK</span></span>|<span data-ttu-id="7559a-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7559a-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="7559a-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7559a-121">E_POINTER</span></span>|<span data-ttu-id="7559a-122">`pwzbuffer` nebo `pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="7559a-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="7559a-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="7559a-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="7559a-124">Vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="7559a-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7559a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7559a-125">Requirements</span></span>  
 <span data-ttu-id="7559a-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7559a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7559a-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7559a-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7559a-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7559a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7559a-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7559a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7559a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7559a-130">See also</span></span>

- [<span data-ttu-id="7559a-131">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7559a-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="7559a-132">Hostování</span><span class="sxs-lookup"><span data-stu-id="7559a-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
