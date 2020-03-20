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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178195"
---
# <a name="getcorversion-function"></a><span data-ttu-id="3e243-102">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="3e243-102">GetCORVersion Function</span></span>
<span data-ttu-id="3e243-103">Vrátí číslo verze běžného jazyka runtime (CLR), který je spuštěn v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="3e243-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="3e243-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3e243-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e243-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e243-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="3e243-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e243-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="3e243-107">Ukazatel na vyrovnávací paměť, ve kterém CLR vrátí řetězec určující verzi runtime, který je aktuálně načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="3e243-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="3e243-108">Vrácený řetězec má stejný tvar jako řetězce předané [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), například "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="3e243-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="3e243-109">Pokud runtime ještě nebyl načten do procesu, funkce vrátí příslušné informace o adresáři pro nejnovější verzi runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="3e243-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="3e243-110">Počet znaků (s),`WCHAR`které mohou `pbuffer`být drženy v .</span><span class="sxs-lookup"><span data-stu-id="3e243-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="3e243-111">Ukazatel na počet znaků skutečně `pbuffer`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="3e243-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="3e243-112">Pokud `pbuffer` je ukazatel null, runtime vrátí E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="3e243-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="3e243-113">Pokud je počet znaků větší než `pbuffer` délka , vrátí doba runtime ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="3e243-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e243-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e243-114">Requirements</span></span>  
 <span data-ttu-id="3e243-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e243-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e243-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e243-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e243-117">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e243-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e243-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e243-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e243-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e243-119">See also</span></span>

- [<span data-ttu-id="3e243-120">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="3e243-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
