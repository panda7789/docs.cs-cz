---
title: "IMetaDataImport::GetFieldMarshal – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce29990bf9e6b5b670a9a277442adac4ceef2947
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="b894f-102">IMetaDataImport::GetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="b894f-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="b894f-103">Získá ukazatel na nativní, nespravovaný typ pole reprezentována token metadata zadané pole.</span><span class="sxs-lookup"><span data-stu-id="b894f-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b894f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b894f-104">Syntax</span></span>  
  
```  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,   
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b894f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b894f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b894f-106">[v] Metadata token, který představuje pole, které chcete získat informace o zařazování spolupráce pro.</span><span class="sxs-lookup"><span data-stu-id="b894f-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="b894f-107">[out] Ukazatel na metadata podpis nativní typu pole.</span><span class="sxs-lookup"><span data-stu-id="b894f-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="b894f-108">[out] Velikost v bajtech `ppvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="b894f-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b894f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b894f-109">Requirements</span></span>  
 <span data-ttu-id="b894f-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b894f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b894f-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b894f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b894f-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b894f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b894f-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b894f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b894f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b894f-114">See Also</span></span>  
 [<span data-ttu-id="b894f-115">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b894f-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b894f-116">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b894f-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
