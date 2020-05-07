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
ms.openlocfilehash: e6c4d5f8cc911198add176cab9c4b9b89128068e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860621"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="ad8df-102">ICLRDataTarget::GetPointerSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ad8df-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="ad8df-103">Získá velikost typu ukazatele, který cílový proces používá, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ad8df-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="ad8df-104">Tato metoda je volána službou Common Language Runtime Data Access Services.</span><span class="sxs-lookup"><span data-stu-id="ad8df-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8df-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad8df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad8df-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad8df-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="ad8df-107">mimo Ukazatel na celočíselnou hodnotu, která určuje velikost ukazatele na cílovém procesu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ad8df-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad8df-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad8df-108">Remarks</span></span>  
 <span data-ttu-id="ad8df-109">Tato metoda je implementována modulem pro ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad8df-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad8df-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad8df-110">Requirements</span></span>  
 <span data-ttu-id="ad8df-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad8df-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad8df-112">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ad8df-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ad8df-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad8df-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad8df-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad8df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8df-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad8df-115">See also</span></span>

- [<span data-ttu-id="ad8df-116">ICLRDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad8df-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
