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
ms.openlocfilehash: d52757f82a950c382c7c8f2162630eda7d7795e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132096"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="80beb-102">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="80beb-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="80beb-103">Vytvoří připojení k proxy serveru ladicího programu, který běží na vzdáleném počítači, a vrátí objekt [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) , který lze použít k dotazování na spuštěné procesy a načtených modulech runtime na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="80beb-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80beb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80beb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80beb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80beb-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="80beb-106">pro Adresa IPv4 vzdáleného cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="80beb-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="80beb-107">mimo Ukazatel na ukazatel na objekt [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) , který se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="80beb-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80beb-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="80beb-108">Return Value</span></span>  
 <span data-ttu-id="80beb-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="80beb-109">S_OK</span></span>  
 <span data-ttu-id="80beb-110">Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="80beb-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="80beb-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="80beb-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="80beb-112">Nelze přidělit dostatek paměti pro `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="80beb-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="80beb-113">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="80beb-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="80beb-114">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="80beb-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80beb-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80beb-115">Requirements</span></span>  
 <span data-ttu-id="80beb-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80beb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80beb-117">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="80beb-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="80beb-118">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="80beb-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="80beb-119">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="80beb-119">**.NET Framework Versions:** 3.5 SP1</span></span>
