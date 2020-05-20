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
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617214"
---
# <a name="getcorversion-function"></a><span data-ttu-id="d5722-102">GetCORVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="d5722-102">GetCORVersion Function</span></span>
<span data-ttu-id="d5722-103">Vrátí číslo verze modulu CLR (Common Language Runtime), který je spuštěn v aktuálním procesu.</span><span class="sxs-lookup"><span data-stu-id="d5722-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="d5722-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d5722-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5722-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5722-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d5722-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5722-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="d5722-107">Ukazatel na vyrovnávací paměť, ve které CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="d5722-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="d5722-108">Vrácený řetězec má stejný tvar jako řetězce předané do [CorBindToRuntimeEx –](corbindtoruntimeex-function.md), například "v 1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="d5722-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="d5722-109">Pokud modul runtime ještě nebyl načten do procesu, vrátí funkce příslušné informace o adresáři pro nejnovější verzi modulu runtime nainstalovaného v počítači.</span><span class="sxs-lookup"><span data-stu-id="d5722-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d5722-110">Počet znaků `WCHAR` , které lze uchovávat v `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="d5722-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d5722-111">Ukazatel na počet skutečně vrácených znaků `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="d5722-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="d5722-112">Pokud `pbuffer` je ukazatel s hodnotou null, modul runtime vrátí E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="d5722-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="d5722-113">Pokud je počet znaků větší než délka `pbuffer` , modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="d5722-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5722-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5722-114">Requirements</span></span>  
 <span data-ttu-id="d5722-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5722-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5722-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5722-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5722-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d5722-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5722-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5722-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5722-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5722-119">See also</span></span>

- [<span data-ttu-id="d5722-120">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="d5722-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
