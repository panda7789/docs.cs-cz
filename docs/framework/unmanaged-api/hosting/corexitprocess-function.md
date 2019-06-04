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
ms.openlocfilehash: 2a28b33f80299ae6fce34f9de66b6f7f1bc70ef6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490563"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="63097-102">CorExitProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="63097-102">CorExitProcess Function</span></span>
<span data-ttu-id="63097-103">Ukončí aktuální nespravovaný proces.</span><span class="sxs-lookup"><span data-stu-id="63097-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="63097-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="63097-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="63097-105">Použití [iclrmetahost::exitprocess –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="63097-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63097-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63097-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63097-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="63097-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="63097-108">Celé číslo, které určuje ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="63097-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63097-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63097-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63097-110">Od verze rozhraní .NET Framework 4, `CorExitProcess` ukončí každý Začínáme modulu runtime v procesu, ne jenom modulu runtime, do kterého byly připojeny starší verze rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="63097-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63097-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63097-111">Requirements</span></span>  
 <span data-ttu-id="63097-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63097-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63097-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63097-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63097-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63097-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63097-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63097-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63097-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63097-116">See also</span></span>

- [<span data-ttu-id="63097-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="63097-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
