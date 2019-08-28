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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d30384ea8b9ff4eee41abd43ae39486f770039e7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041425"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="436fb-102">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="436fb-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="436fb-103">Vrátí instalační adresář modulu CLR (Common Language Runtime), který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="436fb-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="436fb-104">Instalační adresář je plně kvalifikovaný, například "c:\Windows\Microsoft.NET\Framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="436fb-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="436fb-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="436fb-105">This function is deprecated.</span></span> <span data-ttu-id="436fb-106">Je nahrazen metodou [ICLRRuntimeInfo:: GetRuntimeDirectory –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) , která je k dispozici v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="436fb-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="436fb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="436fb-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="436fb-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="436fb-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="436fb-109">mimo Vyrovnávací paměť, ve které modul runtime vrátí řetězec, který obsahuje plně kvalifikovaný název instalačního adresáře pro modul runtime, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="436fb-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="436fb-110">Pokud modul runtime ještě nebyl načten do procesu, vrátí funkce příslušné informace o adresáři pro nejnovější verzi modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="436fb-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="436fb-111">pro Velikost v bajtech `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="436fb-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="436fb-112">mimo Počet znaků vrácených v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="436fb-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="436fb-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="436fb-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="436fb-114">Nepoužívejte tuto funkci v procesech, ve kterých je spuštěna verze 4 modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="436fb-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="436fb-115">Pokud je v počítači nainstalována starší verze modulu CLR, vrátí tato funkce instalační adresář pro danou verzi.</span><span class="sxs-lookup"><span data-stu-id="436fb-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="436fb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="436fb-116">Requirements</span></span>  
 <span data-ttu-id="436fb-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="436fb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="436fb-118">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="436fb-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="436fb-119">**Knihovna** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="436fb-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="436fb-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="436fb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436fb-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="436fb-121">See also</span></span>

- [<span data-ttu-id="436fb-122">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="436fb-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
