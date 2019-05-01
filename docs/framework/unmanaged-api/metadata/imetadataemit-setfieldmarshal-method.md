---
title: IMetaDataEmit::SetFieldMarshal – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82675af85f049aeb288b3dcc18f222c0387a37b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050100"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="bb9eb-102">IMetaDataEmit::SetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="bb9eb-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="bb9eb-103">Nastaví PInvoke zařazovací informace pro parametr pole, metoda návratový nebo metoda odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="bb9eb-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb9eb-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb9eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb9eb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="bb9eb-106">[in] Token pro cíl datová položka.</span><span class="sxs-lookup"><span data-stu-id="bb9eb-106">[in] The token for target data item.</span></span> <span data-ttu-id="bb9eb-107">Je to `mdFieldDef` nebo `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="bb9eb-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="bb9eb-108">[in] Podpis pro nespravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="bb9eb-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="bb9eb-109">[in] Počet bajtů v `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="bb9eb-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb9eb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb9eb-110">Requirements</span></span>  
 <span data-ttu-id="bb9eb-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb9eb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb9eb-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb9eb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb9eb-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb9eb-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb9eb-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb9eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9eb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb9eb-115">See also</span></span>

- [<span data-ttu-id="bb9eb-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb9eb-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bb9eb-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb9eb-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
