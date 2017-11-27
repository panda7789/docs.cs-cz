---
title: "IManagedObject::GetSerializedBuffer – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetSerializedBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d326fba5cbdb38dd2c5d07f4f69f3f2d8e75114c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="6cf79-102">IManagedObject::GetSerializedBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="6cf79-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="6cf79-103">Získá řetězcovou reprezentaci tohoto spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="6cf79-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cf79-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cf79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cf79-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="6cf79-106">[out] Ukazatel na řetězec, který je serializovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="6cf79-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cf79-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cf79-107">Remarks</span></span>  
 <span data-ttu-id="6cf79-108">`GetSerializedBuffer` Metoda serializuje objekt tak můžou být zařazené do klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf79-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cf79-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cf79-109">Requirements</span></span>  
 <span data-ttu-id="6cf79-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf79-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf79-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cf79-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cf79-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cf79-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cf79-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf79-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf79-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cf79-114">See Also</span></span>  
 [<span data-ttu-id="6cf79-115">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cf79-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
