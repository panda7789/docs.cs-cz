---
title: ICorDebugRemoteTarget::GetHostName – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2861a2f0aec66832c618dda7d50dd543920102f4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468600"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="595b7-102">ICorDebugRemoteTarget::GetHostName – metoda</span><span class="sxs-lookup"><span data-stu-id="595b7-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="595b7-103">Vrátí plně kvalifikovaný název domény nebo adresu IPv4 cílového počítače vzdáleného ladění.</span><span class="sxs-lookup"><span data-stu-id="595b7-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="595b7-104">Protokol IPV6 není v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="595b7-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="595b7-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="595b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="595b7-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="595b7-107">[in] Velikost ve znacích, nástroje `szHostName` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="595b7-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="595b7-108">Pokud tento parametr je 0 (nula), `szHostName` musí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="595b7-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="595b7-109">[out] Počet znaků, včetně null zakončení, v názvu hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="595b7-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="595b7-110">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="595b7-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="595b7-111">[out] Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="595b7-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="595b7-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="595b7-112">Return Value</span></span>  
 <span data-ttu-id="595b7-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="595b7-113">S_OK</span></span>  
 <span data-ttu-id="595b7-114">Název hostitele nebo IP adresa byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="595b7-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="595b7-115">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="595b7-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="595b7-116">Nelze vrátit název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="595b7-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="595b7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="595b7-117">Remarks</span></span>  
 <span data-ttu-id="595b7-118">Tato metoda je implementována zapisovačem ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="595b7-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="595b7-119">Je nutné postupovat podle paradigmatu více volání: Při prvním volání volající předá hodnotu null pro obě `cchHostName` a `szHostName`, a `pcchHostName` vrátí velikost požadované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="595b7-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="595b7-120">Při druhém volání je dříve vrácená velikost předána v `cchHostName`, a odpovídající velikosti vyrovnávací paměti je předáno `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="595b7-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="595b7-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="595b7-121">Requirements</span></span>  
 <span data-ttu-id="595b7-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="595b7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="595b7-123">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="595b7-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="595b7-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="595b7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="595b7-125">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="595b7-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595b7-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="595b7-126">See also</span></span>
- [<span data-ttu-id="595b7-127">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="595b7-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="595b7-128">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="595b7-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
