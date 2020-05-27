---
title: IManagedObject::GetSerializedBuffer – metoda
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: c68ec0b41bb38afc7cefaf47df718fffcf42d250
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842425"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="e53b8-102">IManagedObject::GetSerializedBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="e53b8-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="e53b8-103">Získá řetězcovou reprezentaci tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="e53b8-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e53b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e53b8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e53b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e53b8-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="e53b8-106">mimo Ukazatel na řetězec, který je serializovaným objektem.</span><span class="sxs-lookup"><span data-stu-id="e53b8-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e53b8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e53b8-107">Remarks</span></span>  
 <span data-ttu-id="e53b8-108">`GetSerializedBuffer`Metoda serializaci objektu, aby jej bylo možné zařadit do klienta.</span><span class="sxs-lookup"><span data-stu-id="e53b8-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e53b8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e53b8-109">Requirements</span></span>  
 <span data-ttu-id="e53b8-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e53b8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e53b8-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e53b8-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e53b8-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e53b8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e53b8-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e53b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e53b8-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e53b8-114">See also</span></span>

- [<span data-ttu-id="e53b8-115">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e53b8-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
