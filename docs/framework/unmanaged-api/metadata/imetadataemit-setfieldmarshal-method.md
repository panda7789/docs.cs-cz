---
title: "IMetaDataEmit::SetFieldMarshal – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldMarshal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3ef1d50d0d74a92a5bcaf23981226e5a6c852edd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="d6a43-102">IMetaDataEmit::SetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="d6a43-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="d6a43-103">Nastaví PInvoke zařazování informace pro parametr pole, metoda návratový nebo metoda odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="d6a43-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6a43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6a43-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6a43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6a43-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d6a43-106">[v] Token pro cílová data položka.</span><span class="sxs-lookup"><span data-stu-id="d6a43-106">[in] The token for target data item.</span></span> <span data-ttu-id="d6a43-107">To znamená buď `mdFieldDef` nebo `mdParamDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="d6a43-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="d6a43-108">[v] Podpis pro nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="d6a43-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="d6a43-109">[v] Počet bajtů v `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="d6a43-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6a43-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6a43-110">Requirements</span></span>  
 <span data-ttu-id="d6a43-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6a43-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6a43-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6a43-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6a43-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6a43-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6a43-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6a43-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a43-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6a43-115">See Also</span></span>  
 [<span data-ttu-id="d6a43-116">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6a43-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d6a43-117">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6a43-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
