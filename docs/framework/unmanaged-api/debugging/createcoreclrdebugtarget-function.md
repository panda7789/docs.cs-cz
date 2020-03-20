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
ms.openlocfilehash: 0b210f105495fa3f5595adbcb0805e1d1fb62310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179223"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="f0b51-102">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="f0b51-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="f0b51-103">Vytvoří připojení k proxy ladicího programu, který je spuštěn ve vzdáleném počítači, a vrátí objekt [ICoreClrDebugTarget,](icoreclrdebugtarget-interface.md) který lze použít k dotazování spuštěných procesů a načtených runčasech ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="f0b51-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0b51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0b51-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0b51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0b51-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="f0b51-106">[v] Adresa IPv4 vzdáleného cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="f0b51-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="f0b51-107">[out] Ukazatel na ukazatel na objekt [ICoreClrDebugTarget,](icoreclrdebugtarget-interface.md) který bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="f0b51-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0b51-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f0b51-108">Return Value</span></span>  
 <span data-ttu-id="f0b51-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0b51-109">S_OK</span></span>  
 <span data-ttu-id="f0b51-110">Počet CLRs v procesu byl úspěšně určen a odpovídající popisovač a pole cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="f0b51-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="f0b51-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f0b51-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f0b51-112">Nelze přidělit dostatek `ppTarget`paměti pro .</span><span class="sxs-lookup"><span data-stu-id="f0b51-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="f0b51-113">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="f0b51-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f0b51-114">Další selhání.</span><span class="sxs-lookup"><span data-stu-id="f0b51-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0b51-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0b51-115">Requirements</span></span>  
 <span data-ttu-id="f0b51-116">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0b51-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0b51-117">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="f0b51-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f0b51-118">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f0b51-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f0b51-119">**Verze rozhraní .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f0b51-119">**.NET Framework Versions:** 3.5 SP1</span></span>
