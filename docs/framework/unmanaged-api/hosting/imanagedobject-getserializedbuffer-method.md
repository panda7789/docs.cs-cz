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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a94891b91f6ac14469e18ed6840a083ce5e9d64d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516913"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="0b9c0-102">IManagedObject::GetSerializedBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="0b9c0-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="0b9c0-103">Získá řetězcovou reprezentaci tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="0b9c0-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b9c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b9c0-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b9c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b9c0-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="0b9c0-106">[out] Ukazatel na řetězec, který je serializovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="0b9c0-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b9c0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b9c0-107">Remarks</span></span>  
 <span data-ttu-id="0b9c0-108">`GetSerializedBuffer` Metoda serializuje objekt tak může být zařazována do klienta.</span><span class="sxs-lookup"><span data-stu-id="0b9c0-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b9c0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b9c0-109">Requirements</span></span>  
 <span data-ttu-id="0b9c0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b9c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b9c0-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b9c0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b9c0-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b9c0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b9c0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b9c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9c0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b9c0-114">See also</span></span>
- [<span data-ttu-id="0b9c0-115">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b9c0-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
