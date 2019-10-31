---
title: GetCORVersion – funkce
ms.date: 03/30/2017
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
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136424"
---
# <a name="getcorversion-function"></a><span data-ttu-id="1699f-102">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="1699f-102">GetCORVersion Function</span></span>
<span data-ttu-id="1699f-103">Vrátí číslo verze modulu CLR (Common Language Runtime), který je spuštěn v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="1699f-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="1699f-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1699f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1699f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1699f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="1699f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1699f-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="1699f-107">Ukazatel na vyrovnávací paměť, ve které CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="1699f-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="1699f-108">Vrácený řetězec má stejný tvar jako řetězce předané do [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), například "v 1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="1699f-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="1699f-109">Pokud modul runtime ještě nebyl načten do procesu, vrátí funkce příslušné informace o adresáři pro nejnovější verzi modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="1699f-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="1699f-110">Počet znaků (`WCHAR`ů), které lze uchovávat v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="1699f-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="1699f-111">Ukazatel na počet znaků ve skutečnosti vrácených v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="1699f-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="1699f-112">Pokud je `pbuffer` ukazatel s hodnotou null, modul runtime vrátí E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="1699f-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="1699f-113">Pokud je počet znaků větší než délka `pbuffer`, modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="1699f-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1699f-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1699f-114">Requirements</span></span>  
 <span data-ttu-id="1699f-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1699f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1699f-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1699f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1699f-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1699f-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1699f-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1699f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1699f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1699f-119">See also</span></span>

- [<span data-ttu-id="1699f-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1699f-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
