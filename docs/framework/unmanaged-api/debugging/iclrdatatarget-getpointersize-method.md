---
title: ICLRDataTarget::GetPointerSize – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54abcd357c6f26f54432b39bfcb4a0d63afabfe4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738724"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="2c13f-102">ICLRDataTarget::GetPointerSize – metoda</span><span class="sxs-lookup"><span data-stu-id="2c13f-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="2c13f-103">Získá velikost v bajtech, typu ukazatele, který používá cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="2c13f-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="2c13f-104">Tato metoda je volána službami common language runtime přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="2c13f-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c13f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c13f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c13f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c13f-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="2c13f-107">[out] Ukazatel na celočíselnou hodnotu, která určuje velikost v bajtech, ukazatel na cílový proces.</span><span class="sxs-lookup"><span data-stu-id="2c13f-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c13f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c13f-108">Remarks</span></span>  
 <span data-ttu-id="2c13f-109">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c13f-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c13f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c13f-110">Requirements</span></span>  
 <span data-ttu-id="2c13f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c13f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c13f-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2c13f-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2c13f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c13f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c13f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c13f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c13f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c13f-115">See also</span></span>

- [<span data-ttu-id="2c13f-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c13f-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
