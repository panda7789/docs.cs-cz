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
ms.openlocfilehash: fadd1974cd4fa8a51a06700835f46df24e37d7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175769"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="9a1d6-102">IMetaDataEmit::DefineSecurityAttributeSet – metoda</span><span class="sxs-lookup"><span data-stu-id="9a1d6-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="9a1d6-103">Vytvoří sadu oprávnění zabezpečení připojit k objektu odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="9a1d6-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a1d6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a1d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a1d6-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="9a1d6-106">[v] Token, ke kterému jsou připojeny informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9a1d6-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="9a1d6-107">[v] Pole `COR_SECATTR` struktur.</span><span class="sxs-lookup"><span data-stu-id="9a1d6-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="9a1d6-108">[v] Počet prvků v `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="9a1d6-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="9a1d6-109">[out] Pokud se metoda nezdaří, `rSecAttrs` určuje index v prvku, který způsobil problém.</span><span class="sxs-lookup"><span data-stu-id="9a1d6-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1d6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a1d6-110">Requirements</span></span>  
 <span data-ttu-id="9a1d6-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1d6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1d6-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="9a1d6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a1d6-113">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a1d6-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a1d6-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a1d6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1d6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a1d6-115">See also</span></span>

- [<span data-ttu-id="9a1d6-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a1d6-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9a1d6-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a1d6-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
