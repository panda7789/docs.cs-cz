---
title: GetRealProcAddress – funkce
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256afe9a4304654ddb263a0671db7525f3bedcba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429634"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="97a90-102">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="97a90-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="97a90-103">Získá adresu zadanou funkci, která je exportována z nainstalovaných verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="97a90-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="97a90-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97a90-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97a90-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97a90-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97a90-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97a90-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="97a90-107">[v] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="97a90-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="97a90-108">[out] Umístění, která přijímá ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="97a90-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97a90-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97a90-109">Return Value</span></span>  
 <span data-ttu-id="97a90-110">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty definované v CorError.h.</span><span class="sxs-lookup"><span data-stu-id="97a90-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="97a90-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="97a90-111">Return code</span></span>|<span data-ttu-id="97a90-112">Popis</span><span class="sxs-lookup"><span data-stu-id="97a90-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="97a90-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="97a90-113">S_OK</span></span>|<span data-ttu-id="97a90-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="97a90-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="97a90-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="97a90-115">E_POINTER</span></span>|<span data-ttu-id="97a90-116">`ppv` není platný.</span><span class="sxs-lookup"><span data-stu-id="97a90-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="97a90-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="97a90-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="97a90-118">Funkce není exportovali z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="97a90-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97a90-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97a90-119">Requirements</span></span>  
 <span data-ttu-id="97a90-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97a90-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97a90-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97a90-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97a90-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97a90-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97a90-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97a90-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a90-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="97a90-124">See Also</span></span>  
 [<span data-ttu-id="97a90-125">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="97a90-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
