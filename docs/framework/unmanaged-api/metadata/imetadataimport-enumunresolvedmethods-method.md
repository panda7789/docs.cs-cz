---
title: IMetaDataImport::EnumUnresolvedMethods – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfd53309b2b5e96e28e9e063a8adfda430864115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447450"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="dc1b5-102">IMetaDataImport::EnumUnresolvedMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="dc1b5-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="dc1b5-103">Vytvoří výčet MemberDef tokeny představující nerozpoznané metody v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc1b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc1b5-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc1b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc1b5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="dc1b5-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dc1b5-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="dc1b5-108">[out] Pole používá k ukládání MemberDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dc1b5-109">[v] Maximální velikost `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dc1b5-110">[out] Počet MemberDef tokeny, vrátí se v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc1b5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dc1b5-111">Return Value</span></span>  
  
|<span data-ttu-id="dc1b5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc1b5-112">HRESULT</span></span>|<span data-ttu-id="dc1b5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dc1b5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dc1b5-114">`EnumUnresolvedMethods` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dc1b5-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="dc1b5-116">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc1b5-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc1b5-117">Remarks</span></span>  
 <span data-ttu-id="dc1b5-118">Nerozpoznané metoda je ten, který byl deklarován, ale není implementováno.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="dc1b5-119">Metoda je součástí výčtu, pokud je označena jako metodu `miForwardRef` a buď `mdPinvokeImpl` nebo `miRuntime` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="dc1b5-120">Jinými slovy, nerozpoznané metoda je třída metoda, která je označena `miForwardRef` , ale která není implementována v nespravovaném kódu (dosaženo pomocí služby PInvoke) ani interně implementované samotný modul runtime</span><span class="sxs-lookup"><span data-stu-id="dc1b5-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="dc1b5-121">Výčet vyloučí všechny metody, které jsou definované v modulu oboru (globals) nebo rozhraní nebo abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="dc1b5-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1b5-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc1b5-122">Requirements</span></span>  
 <span data-ttu-id="dc1b5-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc1b5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1b5-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc1b5-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc1b5-125">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc1b5-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc1b5-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1b5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1b5-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc1b5-127">See Also</span></span>  
 [<span data-ttu-id="dc1b5-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc1b5-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dc1b5-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc1b5-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
