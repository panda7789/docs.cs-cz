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
ms.openlocfilehash: 44578595b3cb790570c5359e714bd39c109cf1f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176458"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="1f844-102">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="1f844-102">CorExitProcess Function</span></span>
<span data-ttu-id="1f844-103">Ukončí aktuální nespravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="1f844-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="1f844-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1f844-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="1f844-105">Místo toho použijte metodu [ICLRMetaHost::ExitProcess.](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)</span><span class="sxs-lookup"><span data-stu-id="1f844-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f844-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f844-106">Syntax</span></span>  
  
```cpp  
void STDMETHODCALLTYPE CorExitProcess (
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f844-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f844-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="1f844-108">Celé číslo, které určuje kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="1f844-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f844-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f844-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f844-110">Počínaje rozhraním .NET `CorExitProcess` Framework 4 ukončí každý spuštěný čas runtime v procesu, nikoli pouze runtime, ke kterému byla vázána starší rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1f844-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f844-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f844-111">Requirements</span></span>  
 <span data-ttu-id="1f844-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f844-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f844-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f844-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f844-114">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f844-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f844-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f844-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f844-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f844-116">See also</span></span>

- [<span data-ttu-id="1f844-117">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1f844-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
