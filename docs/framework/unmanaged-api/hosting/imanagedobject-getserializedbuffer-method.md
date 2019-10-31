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
ms.openlocfilehash: 4a55ae265230c4da3cc0a19b06a7597be8661beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103251"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="688c7-102">IManagedObject::GetSerializedBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="688c7-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="688c7-103">Získá řetězcovou reprezentaci tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="688c7-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="688c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="688c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="688c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="688c7-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="688c7-106">mimo Ukazatel na řetězec, který je serializovaným objektem.</span><span class="sxs-lookup"><span data-stu-id="688c7-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="688c7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="688c7-107">Remarks</span></span>  
 <span data-ttu-id="688c7-108">Metoda `GetSerializedBuffer` serializaci objektu, aby jej bylo možné zařadit do klienta.</span><span class="sxs-lookup"><span data-stu-id="688c7-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="688c7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="688c7-109">Requirements</span></span>  
 <span data-ttu-id="688c7-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="688c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="688c7-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="688c7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="688c7-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="688c7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="688c7-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="688c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688c7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="688c7-114">See also</span></span>

- [<span data-ttu-id="688c7-115">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="688c7-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
