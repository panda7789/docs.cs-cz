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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0741e5773b946186a452e191cc3ae987e6067c44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606884"
---
# <a name="getcorversion-function"></a><span data-ttu-id="076d7-102">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="076d7-102">GetCORVersion Function</span></span>
<span data-ttu-id="076d7-103">Vrátí číslo verze common language runtime (CLR), na kterém běží v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="076d7-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="076d7-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="076d7-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="076d7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="076d7-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="076d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="076d7-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="076d7-107">Ukazatel do vyrovnávací paměti, ve kterém CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načtená do procesu.</span><span class="sxs-lookup"><span data-stu-id="076d7-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="076d7-108">Vrácený řetězec má stejného formuláře jako řetězce předané [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), například "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="076d7-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="076d7-109">Pokud modul runtime nebylo načteno do procesu, funkce vrátí informace o příslušné adresáře pro nejnovější verzi modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="076d7-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="076d7-110">Počet znaků (`WCHAR`s), která se můžou uchovávat v `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="076d7-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="076d7-111">Ukazatel na počet skutečně vrácených v znaků `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="076d7-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="076d7-112">Pokud `pbuffer` je ukazatel s hodnotou null, vrátí E_POINTER modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="076d7-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="076d7-113">Pokud je větší počet znaků, které pak délka `pbuffer` , modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="076d7-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="076d7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="076d7-114">Requirements</span></span>  
 <span data-ttu-id="076d7-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="076d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="076d7-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="076d7-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="076d7-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="076d7-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="076d7-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="076d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="076d7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="076d7-119">See also</span></span>
- [<span data-ttu-id="076d7-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="076d7-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
