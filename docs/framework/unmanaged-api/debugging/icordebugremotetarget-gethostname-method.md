---
title: "ICorDebugRemoteTarget::GetHostName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45fa4afebda00cb2549a5c18ba81c6bb4e8210e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="57e5d-102">ICorDebugRemoteTarget::GetHostName – metoda</span><span class="sxs-lookup"><span data-stu-id="57e5d-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="57e5d-103">Vrátí plně kvalifikovaný název domény nebo adresu IPv4 vzdáleného ladění cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="57e5d-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="57e5d-104">Protokol IPV6 není podporován v tuto chvíli.</span><span class="sxs-lookup"><span data-stu-id="57e5d-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e5d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57e5d-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57e5d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="57e5d-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="57e5d-107">[v] Velikost v znaků, z `szHostName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="57e5d-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="57e5d-108">Pokud má parametr hodnotu 0 (nula), `szHostName` musí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="57e5d-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="57e5d-109">[out] Počet znaků, včetně zakončením null v názvu hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="57e5d-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="57e5d-110">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="57e5d-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="57e5d-111">[out] Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="57e5d-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57e5d-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="57e5d-112">Return Value</span></span>  
 <span data-ttu-id="57e5d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="57e5d-113">S_OK</span></span>  
 <span data-ttu-id="57e5d-114">Název hostitele nebo IP adresa byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="57e5d-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="57e5d-115">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="57e5d-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="57e5d-116">Nelze vrátit název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="57e5d-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57e5d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57e5d-117">Remarks</span></span>  
 <span data-ttu-id="57e5d-118">Tato metoda je implementována zapisovačem ladicí program.</span><span class="sxs-lookup"><span data-stu-id="57e5d-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="57e5d-119">Musí mít více zlepší volání: při prvním volání volající předá hodnotu null na obě `cchHostName` a `szHostName`, a `pcchHostName` vrátí velikost požadované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="57e5d-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer .</span></span> <span data-ttu-id="57e5d-120">Na druhé volání, je předaná velikost, která byla předtím vrátila `cchHostName`, a je správně velikosti vyrovnávací paměti předaná `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="57e5d-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57e5d-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57e5d-121">Requirements</span></span>  
 <span data-ttu-id="57e5d-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57e5d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57e5d-123">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="57e5d-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="57e5d-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57e5d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57e5d-125">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="57e5d-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e5d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="57e5d-126">See Also</span></span>  
 [<span data-ttu-id="57e5d-127">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e5d-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="57e5d-128">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57e5d-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
