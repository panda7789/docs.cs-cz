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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf3c00eafe47556c6b46e1acb687a19df5a2b28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601753"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="ac610-102">ICLRMetaHost::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="ac610-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="ac610-103">Pokusí se korektně vypnout všechny načtené moduly runtime a poté ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="ac610-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="ac610-104">Nahrazuje [corexitprocess –](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="ac610-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac610-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac610-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac610-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac610-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="ac610-107">[in] Ukončovací kód procesu.</span><span class="sxs-lookup"><span data-stu-id="ac610-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac610-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ac610-108">Return Value</span></span>  
 <span data-ttu-id="ac610-109">Tato metoda nikdy nevrátí, tak její návratová hodnota není definována.</span><span class="sxs-lookup"><span data-stu-id="ac610-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac610-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac610-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac610-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac610-111">Requirements</span></span>  
 <span data-ttu-id="ac610-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac610-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac610-113">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ac610-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ac610-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac610-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac610-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac610-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac610-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac610-116">See also</span></span>
- [<span data-ttu-id="ac610-117">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac610-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="ac610-118">Hostování</span><span class="sxs-lookup"><span data-stu-id="ac610-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
