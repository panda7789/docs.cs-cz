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
ms.openlocfilehash: 48ce5381c745669b813f5b28d801add7daba7825
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470059"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="38568-102">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="38568-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="38568-103">Vytvoří připojení k proxy ladicího programu, který běží na vzdáleném počítači a vrátí [icoreclrdebugtarget –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který můžete použít k dotazování, spuštěné procesy a načtené moduly runtime na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="38568-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38568-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38568-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38568-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38568-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="38568-106">[in] Adresa IPv4 vzdálené cílové počítače.</span><span class="sxs-lookup"><span data-stu-id="38568-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="38568-107">[out] Ukazatel na ukazatel [icoreclrdebugtarget –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="38568-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38568-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38568-108">Return Value</span></span>  
 <span data-ttu-id="38568-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="38568-109">S_OK</span></span>  
 <span data-ttu-id="38568-110">Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.</span><span class="sxs-lookup"><span data-stu-id="38568-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="38568-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="38568-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="38568-112">Nepovedlo se přidělit dostatek paměti pro `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="38568-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="38568-113">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="38568-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="38568-114">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="38568-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38568-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38568-115">Requirements</span></span>  
 <span data-ttu-id="38568-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38568-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38568-117">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="38568-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="38568-118">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="38568-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="38568-119">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="38568-119">**.NET Framework Versions:** 3.5 SP1</span></span>
