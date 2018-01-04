---
title: "GetRealProcAddress – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRealProcAddress
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRealProcAddress
helpviewer_keywords: GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ade1c902d00e991612406041ef0a0b2c1bb884e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="510de-102">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="510de-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="510de-103">Získá adresu zadanou funkci, která je exportována z nainstalovaných verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="510de-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="510de-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="510de-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="510de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="510de-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="510de-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="510de-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="510de-107">[v] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="510de-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="510de-108">[out] Umístění, která přijímá ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="510de-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="510de-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="510de-109">Return Value</span></span>  
 <span data-ttu-id="510de-110">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty definované v CorError.h.</span><span class="sxs-lookup"><span data-stu-id="510de-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="510de-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="510de-111">Return code</span></span>|<span data-ttu-id="510de-112">Popis</span><span class="sxs-lookup"><span data-stu-id="510de-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="510de-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="510de-113">S_OK</span></span>|<span data-ttu-id="510de-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="510de-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="510de-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="510de-115">E_POINTER</span></span>|<span data-ttu-id="510de-116">`ppv`není platný.</span><span class="sxs-lookup"><span data-stu-id="510de-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="510de-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="510de-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="510de-118">Funkce není exportovali z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="510de-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="510de-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="510de-119">Requirements</span></span>  
 <span data-ttu-id="510de-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="510de-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="510de-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="510de-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="510de-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="510de-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="510de-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="510de-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510de-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="510de-124">See Also</span></span>  
 [<span data-ttu-id="510de-125">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="510de-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
