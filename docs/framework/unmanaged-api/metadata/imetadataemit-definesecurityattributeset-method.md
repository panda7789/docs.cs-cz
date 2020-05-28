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
ms.openlocfilehash: c33ede841324820da16e33d35bbf5e8f8e75924f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009363"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="7736d-102">IMetaDataEmit::DefineSecurityAttributeSet – metoda</span><span class="sxs-lookup"><span data-stu-id="7736d-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="7736d-103">Vytvoří sadu oprávnění zabezpečení pro připojení k objektu, na který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="7736d-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7736d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7736d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7736d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7736d-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="7736d-106">pro Token, ke kterému jsou připojeny informace o zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7736d-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="7736d-107">pro Pole `COR_SECATTR` struktur.</span><span class="sxs-lookup"><span data-stu-id="7736d-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="7736d-108">pro Počet prvků v `rSecAttrs` .</span><span class="sxs-lookup"><span data-stu-id="7736d-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="7736d-109">mimo Pokud se metoda nezdařila, určuje index v `rSecAttrs` prvku, který způsobil problém.</span><span class="sxs-lookup"><span data-stu-id="7736d-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7736d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7736d-110">Requirements</span></span>  
 <span data-ttu-id="7736d-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7736d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7736d-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7736d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7736d-113">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7736d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7736d-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7736d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7736d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7736d-115">See also</span></span>

- [<span data-ttu-id="7736d-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7736d-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7736d-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7736d-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
