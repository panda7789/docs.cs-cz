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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95625cfe17b36c0244e6780a08dcf50ce50763d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201855"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="13936-102">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="13936-102">CorExitProcess Function</span></span>
<span data-ttu-id="13936-103">Ukončí aktuální nespravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="13936-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="13936-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13936-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="13936-105">Použití [iclrmetahost::exitprocess –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="13936-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13936-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13936-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13936-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="13936-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="13936-108">Celé číslo, které určuje ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="13936-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13936-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13936-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13936-110">Počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` ukončí každý Začínáme modulu runtime v procesu, ne jenom modulu runtime, do kterého byly připojeny starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="13936-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13936-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13936-111">Requirements</span></span>  
 <span data-ttu-id="13936-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13936-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13936-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13936-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13936-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13936-114">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="13936-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="13936-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13936-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13936-116">See also</span></span>

- [<span data-ttu-id="13936-117">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="13936-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
