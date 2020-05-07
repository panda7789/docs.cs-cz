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
ms.openlocfilehash: 2271611b5cbbfe487e5798be0429ed94c227a67f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860886"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="e5440-102">CreateCoreClrDebugTarget – funkce</span><span class="sxs-lookup"><span data-stu-id="e5440-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="e5440-103">Vytvoří připojení k proxy serveru ladicího programu, který běží na vzdáleném počítači, a vrátí objekt [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , který lze použít k dotazování na spuštěné procesy a načtených modulech runtime na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="e5440-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5440-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5440-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5440-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5440-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="e5440-106">pro Adresa IPv4 vzdáleného cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="e5440-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="e5440-107">mimo Ukazatel na ukazatel na objekt [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) , který se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="e5440-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5440-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5440-108">Return Value</span></span>  
 <span data-ttu-id="e5440-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5440-109">S_OK</span></span>  
 <span data-ttu-id="e5440-110">Počet CLRs v procesu byl úspěšně zjištěn a odpovídající pole popisovače a cesty byly správně vyplněny.</span><span class="sxs-lookup"><span data-stu-id="e5440-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="e5440-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e5440-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e5440-112">Nelze přidělit dostatek paměti pro `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="e5440-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="e5440-113">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="e5440-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e5440-114">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="e5440-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5440-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5440-115">Requirements</span></span>  
 <span data-ttu-id="e5440-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5440-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5440-117">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="e5440-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e5440-118">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="e5440-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e5440-119">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e5440-119">**.NET Framework Versions:** 3.5 SP1</span></span>
