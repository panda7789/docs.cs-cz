---
title: "IMetaDataEmit::DefineSecurityAttributeSet – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineSecurityAttributeSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 79d5bb7240305d06d916e969765606ddc2ddf9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="80977-102">IMetaDataEmit::DefineSecurityAttributeSet – metoda</span><span class="sxs-lookup"><span data-stu-id="80977-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="80977-103">Vytvoří sadu oprávnění zabezpečení pro připojení k objektu, který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="80977-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80977-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80977-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80977-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80977-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="80977-106">[v] Token, ke kterému je připojen informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80977-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="80977-107">[v] Pole `COR_SECATTR` struktury.</span><span class="sxs-lookup"><span data-stu-id="80977-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="80977-108">[v] Počet elementů v `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="80977-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="80977-109">[out] Pokud metoda selže, určuje index v `rSecAttrs` elementu, který způsobil problém.</span><span class="sxs-lookup"><span data-stu-id="80977-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80977-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80977-110">Requirements</span></span>  
 <span data-ttu-id="80977-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80977-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80977-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80977-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80977-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80977-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80977-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80977-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80977-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="80977-115">See Also</span></span>  
 [<span data-ttu-id="80977-116">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80977-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="80977-117">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80977-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
