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
ms.openlocfilehash: ff9827174e43fd62f3a995e9f477c6fff66b227a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449951"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="0b5cc-102">IMetaDataImport::EnumUnresolvedMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="0b5cc-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="0b5cc-103">Vytvoří výčet tokenů memberDef či představujících nerozpoznané metody v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b5cc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b5cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b5cc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0b5cc-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0b5cc-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="0b5cc-108">mimo Pole, které se používá k uložení tokenů memberDef či.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0b5cc-109">pro Maximální velikost `rMethods` pole</span><span class="sxs-lookup"><span data-stu-id="0b5cc-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0b5cc-110">mimo Počet tokenů memberDef či vrácených v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b5cc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0b5cc-111">Return Value</span></span>  
  
|<span data-ttu-id="0b5cc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b5cc-112">HRESULT</span></span>|<span data-ttu-id="0b5cc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0b5cc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0b5cc-114">`EnumUnresolvedMethods` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0b5cc-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0b5cc-116">V takovém případě je `pcTokens` nula.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b5cc-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b5cc-117">Remarks</span></span>  
 <span data-ttu-id="0b5cc-118">Nerozpoznaná metoda je taková, která je deklarovaná, ale není implementovaná.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="0b5cc-119">Metoda je obsažena ve výčtu, pokud je metoda označena `miForwardRef` a buď `mdPinvokeImpl` nebo `miRuntime` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="0b5cc-120">Jinými slovy, nerozpoznaná metoda je metoda třídy, která je označena `miForwardRef`, ale která není implementována v nespravovaném kódu (prostřednictvím PInvoke), ani implementována interně samotným modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="0b5cc-121">Výčet vylučuje všechny metody, které jsou definovány buď v oboru modulu (Globals), nebo v rozhraních nebo abstraktních třídách.</span><span class="sxs-lookup"><span data-stu-id="0b5cc-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5cc-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b5cc-122">Requirements</span></span>  
 <span data-ttu-id="0b5cc-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5cc-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5cc-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b5cc-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b5cc-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b5cc-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b5cc-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b5cc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5cc-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b5cc-127">See also</span></span>

- [<span data-ttu-id="0b5cc-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b5cc-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0b5cc-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b5cc-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
