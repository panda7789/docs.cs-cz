---
title: CorExitProcess – funkce
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
ms.openlocfilehash: a60805e1fd78cb14835957a7afc14fe279cb20fb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616564"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="bc34d-102">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="bc34d-102">CorExitProcess Function</span></span>
<span data-ttu-id="bc34d-103">Ukončí aktuální nespravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="bc34d-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="bc34d-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bc34d-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="bc34d-105">Místo toho použijte metodu [ICLRMetaHost:: ExitProcess –](iclrmetahost-exitprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bc34d-105">Use the [ICLRMetaHost::ExitProcess](iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc34d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc34d-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc34d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc34d-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="bc34d-108">Celé číslo, které určuje ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="bc34d-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc34d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc34d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc34d-110">Počínaje .NET Framework 4 `CorExitProcess` ukončí každý spuštěný modul runtime v procesu, nikoli jenom modul runtime, ke kterému byly navázány starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bc34d-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc34d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc34d-111">Requirements</span></span>  
 <span data-ttu-id="bc34d-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc34d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc34d-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc34d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc34d-114">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bc34d-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc34d-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc34d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc34d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc34d-116">See also</span></span>

- [<span data-ttu-id="bc34d-117">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="bc34d-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
