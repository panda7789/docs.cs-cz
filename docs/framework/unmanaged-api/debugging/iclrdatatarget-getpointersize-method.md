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
ms.openlocfilehash: 80ed86526c99c36254f2b9c71f00483095e771ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734344"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="01b38-102">ICLRDataTarget::GetPointerSize – metoda</span><span class="sxs-lookup"><span data-stu-id="01b38-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="01b38-103">Získá velikost v bajtech, typu ukazatele, který používá cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="01b38-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="01b38-104">Tato metoda je volána službami common language runtime přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="01b38-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b38-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01b38-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01b38-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="01b38-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="01b38-107">[out] Ukazatel na celočíselnou hodnotu, která určuje velikost v bajtech, ukazatel na cílový proces.</span><span class="sxs-lookup"><span data-stu-id="01b38-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01b38-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01b38-108">Remarks</span></span>  
 <span data-ttu-id="01b38-109">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="01b38-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b38-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01b38-110">Requirements</span></span>  
 <span data-ttu-id="01b38-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b38-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b38-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="01b38-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="01b38-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01b38-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01b38-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b38-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b38-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01b38-115">See also</span></span>
- [<span data-ttu-id="01b38-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01b38-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
