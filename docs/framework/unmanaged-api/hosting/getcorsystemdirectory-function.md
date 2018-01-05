---
title: "GetCORSystemDirectory – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02b695ac7f75dd38da8cd06e1444af4ae425ebd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="cddfb-102">GetCORSystemDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="cddfb-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="cddfb-103">Vrátí instalační adresář common language runtime (CLR), který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="cddfb-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="cddfb-104">Instalační adresář je plně kvalifikovaný, například "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="cddfb-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="cddfb-105">Tato funkce je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="cddfb-105">This function is deprecated.</span></span> <span data-ttu-id="cddfb-106">Je nahrazena [iclrruntimeinfo::getruntimedirectory –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metody, které jsou součástí [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cddfb-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cddfb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cddfb-107">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="cddfb-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="cddfb-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="cddfb-109">[out] Vyrovnávací paměť, ve kterém modulu runtime vrátí řetězec, který obsahuje plně kvalifikovaný název instalační adresář pro modul runtime, který je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="cddfb-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="cddfb-110">Pokud modul runtime dosud nebyla načtena do procesu, funkce vrátí informace příslušný adresář na nejnovější verzi modulu runtime v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="cddfb-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="cddfb-111">[v] Velikost v bajtech z `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="cddfb-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="cddfb-112">[out] Počet znaků, vrátí se v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="cddfb-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cddfb-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cddfb-113">Remarks</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cddfb-114">Nepoužívejte tuto funkci v procesy, které používají 4 verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cddfb-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="cddfb-115">Pokud v počítači je nainstalovaná starší verze modulu CLR, vrátí tato funkce instalační adresář pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="cddfb-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddfb-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cddfb-116">Requirements</span></span>  
 <span data-ttu-id="cddfb-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cddfb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cddfb-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cddfb-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cddfb-119">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cddfb-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cddfb-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cddfb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddfb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="cddfb-121">See Also</span></span>  
 [<span data-ttu-id="cddfb-122">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="cddfb-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
