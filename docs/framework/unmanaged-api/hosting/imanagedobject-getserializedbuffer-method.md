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
ms.openlocfilehash: cb9242160b684b3c7b90756d7b20811ad162fc30
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156140"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="36287-102">IManagedObject::GetSerializedBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="36287-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="36287-103">Získá řetězcovou reprezentaci tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="36287-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36287-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36287-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36287-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36287-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="36287-106">[out] Ukazatel na řetězec, který je serializovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="36287-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36287-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36287-107">Remarks</span></span>  
 <span data-ttu-id="36287-108">`GetSerializedBuffer` Metoda serializuje objekt tak může být zařazována do klienta.</span><span class="sxs-lookup"><span data-stu-id="36287-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36287-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36287-109">Requirements</span></span>  
 <span data-ttu-id="36287-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36287-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36287-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36287-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36287-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36287-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36287-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36287-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36287-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36287-114">See also</span></span>

- [<span data-ttu-id="36287-115">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36287-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
