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
ms.openlocfilehash: 18733c2d643a75f9bb11159ba4acdbc8ab064c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404100"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="a276c-102">ICLRDataTarget::SetTLSValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a276c-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="a276c-103">Nastaví hodnotu v místní úložiště vláken (TLS) zadaný vlákna v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="a276c-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="a276c-104">Tato metoda je volána běžné data přístupu služby modulu runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="a276c-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a276c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a276c-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a276c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a276c-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a276c-107">[v] Identifikátor operačního systému vlákna v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="a276c-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="a276c-108">[v] Index umístění.</span><span class="sxs-lookup"><span data-stu-id="a276c-108">[in] The index of the location.</span></span> <span data-ttu-id="a276c-109">Tato hodnota musí být platný index v místním úložišti zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="a276c-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="a276c-110">[v] A `CLRDATA_ADDRESS` hodnotu, která určuje hodnotu umístit v daném umístění TLS.</span><span class="sxs-lookup"><span data-stu-id="a276c-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a276c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a276c-111">Remarks</span></span>  
 <span data-ttu-id="a276c-112">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a276c-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a276c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a276c-113">Requirements</span></span>  
 <span data-ttu-id="a276c-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a276c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a276c-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a276c-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a276c-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a276c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a276c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a276c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a276c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a276c-118">See Also</span></span>  
 [<span data-ttu-id="a276c-119">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a276c-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
