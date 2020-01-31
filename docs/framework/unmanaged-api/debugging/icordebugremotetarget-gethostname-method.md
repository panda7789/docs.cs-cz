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
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791951"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="a8eb5-102">ICorDebugRemoteTarget::GetHostName – metoda</span><span class="sxs-lookup"><span data-stu-id="a8eb5-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="a8eb5-103">Vrátí plně kvalifikovaný název domény nebo IPv4 adresu cílového počítače vzdáleného ladění.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="a8eb5-104">Protokol IPV6 se v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8eb5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8eb5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8eb5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8eb5-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="a8eb5-107">pro Velikost vyrovnávací paměti `szHostName` v znacích.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="a8eb5-108">Pokud je tento parametr 0 (nula), `szHostName` musí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="a8eb5-109">mimo Počet znaků, včetně ukončovacího znaku null, v názvu hostitele nebo IP adrese.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="a8eb5-110">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="a8eb5-111">mimo Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8eb5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8eb5-112">Return Value</span></span>  
 <span data-ttu-id="a8eb5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8eb5-113">S_OK</span></span>  
 <span data-ttu-id="a8eb5-114">Název hostitele nebo IP adresa se úspěšně vrátily.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="a8eb5-115">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="a8eb5-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a8eb5-116">Nelze vrátit název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8eb5-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8eb5-117">Remarks</span></span>  
 <span data-ttu-id="a8eb5-118">Tato metoda je implementována pomocí zapisovače ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="a8eb5-119">Musí následovat za vícenásobnými paradigma volání: při prvním volání volající předává hodnotu null do obou `cchHostName` i `szHostName`a `pcchHostName` vrací velikost požadované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="a8eb5-120">Při druhém volání je výše vrácená velikost předána do `cchHostName`a v `szHostName`předává patřičnou velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a8eb5-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8eb5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8eb5-121">Requirements</span></span>  
 <span data-ttu-id="a8eb5-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8eb5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8eb5-123">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="a8eb5-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a8eb5-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8eb5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8eb5-125">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a8eb5-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8eb5-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8eb5-126">See also</span></span>

- [<span data-ttu-id="a8eb5-127">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8eb5-127">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="a8eb5-128">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8eb5-128">ICorDebug Interface</span></span>](icordebug-interface.md)
