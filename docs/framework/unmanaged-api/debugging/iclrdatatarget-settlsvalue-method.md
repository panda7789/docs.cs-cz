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
ms.openlocfilehash: 6e6e157c7176a0f4f1ad3c585977e2cfb31c33d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793691"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="9efac-102">ICLRDataTarget::SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="9efac-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="9efac-103">Nastaví hodnotu v thread local Storage (TLS) zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="9efac-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="9efac-104">Tato metoda je volána službou Common Language Runtime (CLR) pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="9efac-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9efac-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9efac-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9efac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9efac-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="9efac-107">pro Identifikátor operačního systému vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="9efac-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="9efac-108">pro Index umístění.</span><span class="sxs-lookup"><span data-stu-id="9efac-108">[in] The index of the location.</span></span> <span data-ttu-id="9efac-109">Tato hodnota musí být platný index v místním úložišti zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="9efac-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="9efac-110">pro Hodnota `CLRDATA_ADDRESS`, která určuje hodnotu, která má být umístěna v daném umístění protokolu TLS.</span><span class="sxs-lookup"><span data-stu-id="9efac-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9efac-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9efac-111">Remarks</span></span>  
 <span data-ttu-id="9efac-112">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9efac-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9efac-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9efac-113">Requirements</span></span>  
 <span data-ttu-id="9efac-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9efac-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9efac-115">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9efac-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9efac-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9efac-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9efac-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9efac-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9efac-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9efac-118">See also</span></span>

- [<span data-ttu-id="9efac-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9efac-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
