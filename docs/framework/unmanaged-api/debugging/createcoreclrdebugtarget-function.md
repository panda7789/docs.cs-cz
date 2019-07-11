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
ms.openlocfilehash: dbcf6c842e7eee55609a9ea2a25cda4360f8dc95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739288"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="42cec-102">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="42cec-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="42cec-103">Vytvoří připojení k proxy ladicího programu, který běží na vzdáleném počítači a vrátí [icoreclrdebugtarget –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který můžete použít k dotazování, spuštěné procesy a načtené moduly runtime na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="42cec-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42cec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42cec-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42cec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42cec-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="42cec-106">[in] Adresa IPv4 vzdálené cílové počítače.</span><span class="sxs-lookup"><span data-stu-id="42cec-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="42cec-107">[out] Ukazatel na ukazatel [icoreclrdebugtarget –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objekt, který bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="42cec-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42cec-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42cec-108">Return Value</span></span>  
 <span data-ttu-id="42cec-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="42cec-109">S_OK</span></span>  
 <span data-ttu-id="42cec-110">Úspěšně bylo zjištěno číslo CLRs v procesu a odpovídající popisovač a pole cesty byly správně vyplněné.</span><span class="sxs-lookup"><span data-stu-id="42cec-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="42cec-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="42cec-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="42cec-112">Nepovedlo se přidělit dostatek paměti pro `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="42cec-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="42cec-113">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="42cec-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="42cec-114">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="42cec-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42cec-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42cec-115">Requirements</span></span>  
 <span data-ttu-id="42cec-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42cec-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42cec-117">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="42cec-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="42cec-118">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="42cec-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="42cec-119">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="42cec-119">**.NET Framework Versions:** 3.5 SP1</span></span>
