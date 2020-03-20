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
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178164"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="f0441-102">GetRealProcAddress – funkce</span><span class="sxs-lookup"><span data-stu-id="f0441-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="f0441-103">Získá adresu zadané funkce, která je exportována z nejnovější nainstalované verze clr (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="f0441-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="f0441-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f0441-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0441-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0441-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0441-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0441-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="f0441-107">[v] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="f0441-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f0441-108">[out] Umístění, které obdrží ukazatel na adresu funkce.</span><span class="sxs-lookup"><span data-stu-id="f0441-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0441-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f0441-109">Return Value</span></span>  
 <span data-ttu-id="f0441-110">Tato metoda vrátí standardní kódy chyb ový model COM (COM), jak jsou definovány v souboru WinError.h, kromě následujících hodnot definovaných v souboru CorError.h.</span><span class="sxs-lookup"><span data-stu-id="f0441-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="f0441-111">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="f0441-111">Return code</span></span>|<span data-ttu-id="f0441-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f0441-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f0441-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0441-113">S_OK</span></span>|<span data-ttu-id="f0441-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f0441-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="f0441-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f0441-115">E_POINTER</span></span>|<span data-ttu-id="f0441-116">`ppv`není platný.</span><span class="sxs-lookup"><span data-stu-id="f0441-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="f0441-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="f0441-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="f0441-118">Funkce není exportována z běhu.</span><span class="sxs-lookup"><span data-stu-id="f0441-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0441-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0441-119">Requirements</span></span>  
 <span data-ttu-id="f0441-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0441-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0441-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0441-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0441-122">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0441-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0441-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0441-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0441-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0441-124">See also</span></span>

- [<span data-ttu-id="f0441-125">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f0441-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
