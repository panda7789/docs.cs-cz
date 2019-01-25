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
ms.openlocfilehash: 5a3c1aad3bcd6151267671122fb21772082e15cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658777"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="86823-102">ICLRDataTarget::SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="86823-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="86823-103">Nastaví hodnotu v místním úložišti vláken (TLS) ze zadaného vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="86823-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="86823-104">Tato metoda je volána službami common language runtime (CLR) přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="86823-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86823-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86823-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86823-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="86823-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="86823-107">[in] Operační systém identifikátor vlákna v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="86823-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="86823-108">[in] Index umístění.</span><span class="sxs-lookup"><span data-stu-id="86823-108">[in] The index of the location.</span></span> <span data-ttu-id="86823-109">Tato hodnota musí být platný index v místním úložišti ze zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="86823-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="86823-110">[in] A `CLRDATA_ADDRESS` hodnotu, která určuje hodnotu umístit do daného umístění protokolu TLS.</span><span class="sxs-lookup"><span data-stu-id="86823-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86823-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86823-111">Remarks</span></span>  
 <span data-ttu-id="86823-112">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="86823-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86823-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86823-113">Requirements</span></span>  
 <span data-ttu-id="86823-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86823-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86823-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="86823-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="86823-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86823-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86823-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86823-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86823-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86823-118">See also</span></span>
- [<span data-ttu-id="86823-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86823-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
