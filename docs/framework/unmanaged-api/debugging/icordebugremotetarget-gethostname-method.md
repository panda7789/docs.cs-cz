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
ms.openlocfilehash: 020724c422af7cba0165e6f37d0eacb7742153ec
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379263"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="c1c24-102">ICorDebugRemoteTarget::GetHostName – metoda</span><span class="sxs-lookup"><span data-stu-id="c1c24-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="c1c24-103">Vrátí plně kvalifikovaný název domény nebo IPv4 adresu cílového počítače vzdáleného ladění.</span><span class="sxs-lookup"><span data-stu-id="c1c24-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="c1c24-104">Protokol IPV6 se v tuto chvíli nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="c1c24-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1c24-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1c24-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1c24-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="c1c24-107">pro Velikost `szHostName` vyrovnávací paměti ve znacích.</span><span class="sxs-lookup"><span data-stu-id="c1c24-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="c1c24-108">Pokud je tento parametr 0 (nula), `szHostName` musí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c1c24-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="c1c24-109">mimo Počet znaků, včetně ukončovacího znaku null, v názvu hostitele nebo IP adrese.</span><span class="sxs-lookup"><span data-stu-id="c1c24-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="c1c24-110">Tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c1c24-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="c1c24-111">mimo Vyrovnávací paměť, která obsahuje název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="c1c24-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1c24-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1c24-112">Return Value</span></span>  
 <span data-ttu-id="c1c24-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1c24-113">S_OK</span></span>  
 <span data-ttu-id="c1c24-114">Název hostitele nebo IP adresa se úspěšně vrátily.</span><span class="sxs-lookup"><span data-stu-id="c1c24-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="c1c24-115">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="c1c24-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c1c24-116">Nelze vrátit název hostitele nebo IP adresu.</span><span class="sxs-lookup"><span data-stu-id="c1c24-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1c24-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1c24-117">Remarks</span></span>  
 <span data-ttu-id="c1c24-118">Tato metoda je implementována pomocí zapisovače ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="c1c24-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="c1c24-119">Musí následovat za vícenásobnými paradigma volání: při prvním volání volající předává hodnotu null do a a `cchHostName` `szHostName` `pcchHostName` vrátí velikost požadované vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c1c24-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="c1c24-120">Při druhém volání je výše předána velikost, která byla dříve vrácena `cchHostName` , a předána odpovídající velikost vyrovnávací paměti `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="c1c24-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1c24-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1c24-121">Requirements</span></span>  
 <span data-ttu-id="c1c24-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1c24-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1c24-123">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="c1c24-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c1c24-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c1c24-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1c24-125">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c1c24-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c24-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1c24-126">See also</span></span>

- [<span data-ttu-id="c1c24-127">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1c24-127">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="c1c24-128">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1c24-128">ICorDebug Interface</span></span>](icordebug-interface.md)
