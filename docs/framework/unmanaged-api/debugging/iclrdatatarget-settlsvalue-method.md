---
title: "ICLRDataTarget::SetTLSValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c9d25b496e300d66844e3fd88655ab38da4b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="301fb-102">ICLRDataTarget::SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="301fb-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="301fb-103">Nastaví hodnotu v místní úložiště vláken (TLS) zadaný vlákna v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="301fb-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="301fb-104">Tato metoda je volána běžné data přístupu služby modulu runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="301fb-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="301fb-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="301fb-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="301fb-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="301fb-107">[v] Identifikátor operačního systému vlákna v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="301fb-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="301fb-108">[v] Index umístění.</span><span class="sxs-lookup"><span data-stu-id="301fb-108">[in] The index of the location.</span></span> <span data-ttu-id="301fb-109">Tato hodnota musí být platný index v místním úložišti zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="301fb-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="301fb-110">[v] A `CLRDATA_ADDRESS` hodnotu, která určuje hodnotu umístit v daném umístění TLS.</span><span class="sxs-lookup"><span data-stu-id="301fb-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="301fb-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="301fb-111">Remarks</span></span>  
 <span data-ttu-id="301fb-112">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="301fb-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="301fb-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="301fb-113">Requirements</span></span>  
 <span data-ttu-id="301fb-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="301fb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="301fb-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="301fb-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="301fb-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="301fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="301fb-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="301fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301fb-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="301fb-118">See Also</span></span>  
 [<span data-ttu-id="301fb-119">ICLRDataTarget – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="301fb-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
