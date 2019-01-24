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
ms.openlocfilehash: b31db6e6a8ecb3fa15f1a8690b007bdb536b97c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506547"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="cff5f-102">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="cff5f-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="cff5f-103">Získá adresu zadané funkce, která je exportována z poslední instalované verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="cff5f-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="cff5f-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cff5f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff5f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff5f-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cff5f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cff5f-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="cff5f-107">[in] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="cff5f-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="cff5f-108">[out] Umístění, která přijímá ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="cff5f-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cff5f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cff5f-109">Return Value</span></span>  
 <span data-ttu-id="cff5f-110">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot definovaných v CorError.h.</span><span class="sxs-lookup"><span data-stu-id="cff5f-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="cff5f-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="cff5f-111">Return code</span></span>|<span data-ttu-id="cff5f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="cff5f-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cff5f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="cff5f-113">S_OK</span></span>|<span data-ttu-id="cff5f-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="cff5f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="cff5f-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cff5f-115">E_POINTER</span></span>|<span data-ttu-id="cff5f-116">`ppv` není platný.</span><span class="sxs-lookup"><span data-stu-id="cff5f-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="cff5f-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="cff5f-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="cff5f-118">Funkce není exportována z modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cff5f-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cff5f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cff5f-119">Requirements</span></span>  
 <span data-ttu-id="cff5f-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff5f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff5f-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cff5f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cff5f-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cff5f-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cff5f-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff5f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff5f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cff5f-124">See also</span></span>
- [<span data-ttu-id="cff5f-125">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="cff5f-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
