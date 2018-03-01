---
title: "GetCORVersion – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c61dd0b10bc0229d8f0d7dd4f6357ddaf5986637
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getcorversion-function"></a><span data-ttu-id="2e509-102">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="2e509-102">GetCORVersion Function</span></span>
<span data-ttu-id="2e509-103">Vrátí číslo verze common language runtime (CLR), který běží v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="2e509-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="2e509-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e509-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e509-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e509-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e509-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e509-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="2e509-107">Ukazatel na vyrovnávací paměť, ve kterém modulu CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načtený do procesu.</span><span class="sxs-lookup"><span data-stu-id="2e509-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="2e509-108">Vrácený řetězec používá stejný formát jako řetězce předaný [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), například "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="2e509-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="2e509-109">Pokud modul runtime dosud nebyla načtena do procesu, funkce vrátí informace příslušný adresář na nejnovější verzi modulu runtime v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="2e509-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2e509-110">Počet znaků (`WCHAR`s), můžete uchovávat v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="2e509-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2e509-111">Ukazatel na počet znaků, které jsou ve skutečnosti, vrátí se v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="2e509-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="2e509-112">Pokud `pbuffer` je ukazatel s hodnotou null, vrátí E_POINTER modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2e509-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="2e509-113">Pokud je větší počet znaků, pak délka `pbuffer` , modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="2e509-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e509-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e509-114">Requirements</span></span>  
 <span data-ttu-id="2e509-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e509-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e509-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e509-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e509-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e509-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e509-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e509-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e509-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e509-119">See Also</span></span>  
 [<span data-ttu-id="2e509-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="2e509-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
