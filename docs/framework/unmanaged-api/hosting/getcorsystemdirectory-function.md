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
ms.openlocfilehash: 567e6533a9a9ac718f8b5acac769295c104f7f3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144323"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="f28d3-102">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="f28d3-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="f28d3-103">Vrátí instalační adresář modulu common language runtime (CLR), který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="f28d3-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="f28d3-104">Instalační adresář je plně kvalifikovaný, například "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="f28d3-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="f28d3-105">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f28d3-105">This function is deprecated.</span></span> <span data-ttu-id="f28d3-106">Je nahrazen technologií [iclrruntimeinfo::getruntimedirectory –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metoda součástí [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f28d3-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f28d3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f28d3-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="f28d3-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f28d3-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="f28d3-109">[out] Vyrovnávací paměť, ve kterém modul runtime vrátí řetězec, který obsahuje plně kvalifikovaný název v instalačním adresáři pro modul runtime, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="f28d3-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="f28d3-110">Pokud modul runtime nebylo načteno do procesu, funkce vrátí informace o příslušné adresáře pro nejnovější verzi modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="f28d3-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f28d3-111">[in] Velikost v bajtech, z `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="f28d3-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f28d3-112">[out] Počet znaků, které jsou vráceny v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="f28d3-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f28d3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f28d3-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f28d3-114">Nepoužívejte tuto funkci v procesy, které jsou spuštěny modulu CLR verze 4.</span><span class="sxs-lookup"><span data-stu-id="f28d3-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="f28d3-115">Pokud v počítači je nainstalovaná starší verzi modulu CLR, tato funkce vrátí instalační adresář pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="f28d3-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f28d3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f28d3-116">Requirements</span></span>  
 <span data-ttu-id="f28d3-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f28d3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f28d3-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f28d3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f28d3-119">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f28d3-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f28d3-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f28d3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f28d3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f28d3-121">See also</span></span>

- [<span data-ttu-id="f28d3-122">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f28d3-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
