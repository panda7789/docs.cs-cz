---
title: CreateCoreClrDebugTarget – funkce
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a957eb6907b55fe948d696a6a25076c3950f7381
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402972"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="e3efc-102">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="e3efc-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="e3efc-103">Vytvoří připojení k proxy server ladicí program, který běží na vzdáleném počítači a vrátí [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který můžete použít k dotazování spuštěných procesů a načíst moduly runtime ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="e3efc-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3efc-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3efc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3efc-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="e3efc-106">[v] IPv4 adresu vzdáleného cílový počítač.</span><span class="sxs-lookup"><span data-stu-id="e3efc-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="e3efc-107">[out] Ukazatel na ukazatel na [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="e3efc-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3efc-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e3efc-108">Return Value</span></span>  
 <span data-ttu-id="e3efc-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3efc-109">S_OK</span></span>  
 <span data-ttu-id="e3efc-110">Počet CLRs v procesu byla úspěšně zjistit a byly správně zadat odpovídající popisovač a cesta pole.</span><span class="sxs-lookup"><span data-stu-id="e3efc-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="e3efc-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e3efc-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e3efc-112">Nelze přidělit dostatek paměti pro `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="e3efc-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="e3efc-113">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="e3efc-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e3efc-114">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="e3efc-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3efc-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3efc-115">Requirements</span></span>  
 <span data-ttu-id="e3efc-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3efc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3efc-117">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e3efc-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e3efc-118">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e3efc-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e3efc-119">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e3efc-119">**.NET Framework Versions:** 3.5 SP1</span></span>
