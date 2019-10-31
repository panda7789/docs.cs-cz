---
title: ICLRDataTarget::SetTLSValue – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
ms.openlocfilehash: 1425d48bb18d4161a1c96239b76b8315ae258705
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112781"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="193ba-102">ICLRDataTarget::SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="193ba-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="193ba-103">Nastaví hodnotu v thread local Storage (TLS) zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="193ba-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="193ba-104">Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="193ba-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="193ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="193ba-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="193ba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="193ba-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="193ba-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="193ba-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="193ba-108">pro Index umístění.</span><span class="sxs-lookup"><span data-stu-id="193ba-108">[in] The index of the location.</span></span> <span data-ttu-id="193ba-109">Tato hodnota musí být platný index v místním úložišti zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="193ba-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="193ba-110">pro Hodnota `CLRDATA_ADDRESS`, která určuje hodnotu, která má být umístěna v daném umístění protokolu TLS.</span><span class="sxs-lookup"><span data-stu-id="193ba-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="193ba-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="193ba-111">Remarks</span></span>  
 <span data-ttu-id="193ba-112">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="193ba-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="193ba-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="193ba-113">Requirements</span></span>  
 <span data-ttu-id="193ba-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="193ba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="193ba-115">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="193ba-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="193ba-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="193ba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="193ba-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="193ba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193ba-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="193ba-118">See also</span></span>

- [<span data-ttu-id="193ba-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="193ba-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
