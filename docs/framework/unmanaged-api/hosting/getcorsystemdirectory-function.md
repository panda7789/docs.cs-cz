---
title: GetCORSystemDirectory – funkce
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178208"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="1565d-102">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="1565d-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="1565d-103">Vrátí instalační adresář clr (COMMON Language runtime), který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="1565d-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="1565d-104">Instalační adresář je plně kvalifikovaný, například "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="1565d-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="1565d-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1565d-105">This function is deprecated.</span></span> <span data-ttu-id="1565d-106">Je nahrazen metodou [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) poskytnutou v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1565d-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1565d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1565d-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="1565d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1565d-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="1565d-109">[out] Vyrovnávací paměť, ve které runtime vrátí řetězec, který obsahuje plně kvalifikovaný název instalačního adresáře pro runtime, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="1565d-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="1565d-110">Pokud runtime ještě nebyl načten do procesu, funkce vrátí příslušné informace o adresáři pro nejnovější verzi runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="1565d-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="1565d-111">[v] Velikost v bajtů `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="1565d-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="1565d-112">[out] Počet znaků vrácených `pbuffer`v .</span><span class="sxs-lookup"><span data-stu-id="1565d-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1565d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1565d-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1565d-114">Nepoužívejte tuto funkci v procesech, které jsou spuštěny verze 4 CLR.</span><span class="sxs-lookup"><span data-stu-id="1565d-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="1565d-115">Pokud je v počítači nainstalována starší verze nařízení CLR, vrátí tato funkce instalační adresář pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="1565d-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1565d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1565d-116">Requirements</span></span>  
 <span data-ttu-id="1565d-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1565d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1565d-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1565d-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1565d-119">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1565d-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1565d-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1565d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1565d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1565d-121">See also</span></span>

- [<span data-ttu-id="1565d-122">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1565d-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
