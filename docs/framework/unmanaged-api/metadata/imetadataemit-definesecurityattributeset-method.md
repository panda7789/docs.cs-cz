---
title: IMetaDataEmit::DefineSecurityAttributeSet – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 483f59ee3e81861ec1b05a0fee9c5db797aab68f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491143"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="0fa0c-102">IMetaDataEmit::DefineSecurityAttributeSet – metoda</span><span class="sxs-lookup"><span data-stu-id="0fa0c-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="0fa0c-103">Vytvoří sadu oprávnění zabezpečení k připojení k objekt odkazovaný zadaným parametrem zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="0fa0c-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fa0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fa0c-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fa0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fa0c-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="0fa0c-106">[in] Token, ke kterému je připojený informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0fa0c-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="0fa0c-107">[in] Pole `COR_SECATTR` struktury.</span><span class="sxs-lookup"><span data-stu-id="0fa0c-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="0fa0c-108">[in] Počet prvků v `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="0fa0c-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="0fa0c-109">[out] Jestliže metoda selže, určuje index v `rSecAttrs` elementu, který způsobil problém.</span><span class="sxs-lookup"><span data-stu-id="0fa0c-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fa0c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fa0c-110">Requirements</span></span>  
 <span data-ttu-id="0fa0c-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fa0c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fa0c-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0fa0c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fa0c-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fa0c-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fa0c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fa0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fa0c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fa0c-115">See also</span></span>
- [<span data-ttu-id="0fa0c-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0fa0c-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0fa0c-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0fa0c-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
