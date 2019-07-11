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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34c0ab32d18d5aeeb81befa736cc42b678b11fb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738549"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="a717f-102">ICLRDataTarget::SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a717f-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="a717f-103">Nastaví hodnotu v místním úložišti vláken (TLS) ze zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="a717f-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="a717f-104">Tato metoda je volána službami common language runtime (CLR) přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="a717f-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a717f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a717f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a717f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a717f-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a717f-107">[in] Operační systém identifikátor vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="a717f-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="a717f-108">[in] Index umístění.</span><span class="sxs-lookup"><span data-stu-id="a717f-108">[in] The index of the location.</span></span> <span data-ttu-id="a717f-109">Tato hodnota musí být platný index v místním úložišti ze zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="a717f-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="a717f-110">[in] A `CLRDATA_ADDRESS` hodnotu, která určuje hodnotu umístit do daného umístění protokolu TLS.</span><span class="sxs-lookup"><span data-stu-id="a717f-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a717f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a717f-111">Remarks</span></span>  
 <span data-ttu-id="a717f-112">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a717f-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a717f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a717f-113">Requirements</span></span>  
 <span data-ttu-id="a717f-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a717f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a717f-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a717f-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a717f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a717f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a717f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a717f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a717f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a717f-118">See also</span></span>

- [<span data-ttu-id="a717f-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a717f-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
