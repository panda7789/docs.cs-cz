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
ms.openlocfilehash: 3f244d256d3af104d1d0c65769e82a87d6de046e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189007"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="621e9-102">IMetaDataEmit::DefineSecurityAttributeSet – metoda</span><span class="sxs-lookup"><span data-stu-id="621e9-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="621e9-103">Vytvoří sadu oprávnění zabezpečení k připojení k objekt odkazovaný zadaným parametrem zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="621e9-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="621e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="621e9-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="621e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="621e9-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="621e9-106">[in] Token, ke kterému je připojený informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="621e9-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="621e9-107">[in] Pole `COR_SECATTR` struktury.</span><span class="sxs-lookup"><span data-stu-id="621e9-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="621e9-108">[in] Počet prvků v `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="621e9-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="621e9-109">[out] Jestliže metoda selže, určuje index v `rSecAttrs` elementu, který způsobil problém.</span><span class="sxs-lookup"><span data-stu-id="621e9-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="621e9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="621e9-110">Requirements</span></span>  
 <span data-ttu-id="621e9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="621e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="621e9-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="621e9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="621e9-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="621e9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="621e9-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="621e9-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="621e9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="621e9-115">See also</span></span>

- [<span data-ttu-id="621e9-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="621e9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="621e9-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="621e9-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
