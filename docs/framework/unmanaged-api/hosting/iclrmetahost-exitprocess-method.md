---
title: ICLRMetaHost::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 83cbfa097541681305ff285f21c2b6c9c6391ef8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703758"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="705fe-102">ICLRMetaHost::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="705fe-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="705fe-103">Pokusí se řádně vypnout všechny načtené běhové moduly a pak proces ukončí.</span><span class="sxs-lookup"><span data-stu-id="705fe-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="705fe-104">Nahrazuje funkci [CorExitProcess –](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="705fe-104">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705fe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="705fe-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="705fe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="705fe-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="705fe-107">pro Ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="705fe-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="705fe-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="705fe-108">Return Value</span></span>  
 <span data-ttu-id="705fe-109">Tato metoda se nikdy nevrátí, takže vrácená hodnota je nedefinovaná.</span><span class="sxs-lookup"><span data-stu-id="705fe-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="705fe-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="705fe-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705fe-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="705fe-111">Requirements</span></span>  
 <span data-ttu-id="705fe-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="705fe-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705fe-113">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="705fe-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="705fe-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="705fe-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="705fe-115">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705fe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705fe-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="705fe-116">See also</span></span>

- [<span data-ttu-id="705fe-117">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="705fe-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="705fe-118">Hostování</span><span class="sxs-lookup"><span data-stu-id="705fe-118">Hosting</span></span>](index.md)
