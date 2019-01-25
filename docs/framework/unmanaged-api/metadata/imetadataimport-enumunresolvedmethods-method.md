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
ms.openlocfilehash: 2009104d31723b9fed383b7bbb41146127d89bd0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611953"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="4a5e6-102">IMetaDataImport::EnumUnresolvedMethods – metoda</span><span class="sxs-lookup"><span data-stu-id="4a5e6-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="4a5e6-103">Vytvoří výčet MemberDef tokeny představující nevyřešené metody v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a5e6-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a5e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a5e6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4a5e6-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4a5e6-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="4a5e6-108">[out] Pole pro ukládání tokenů MemberDef.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4a5e6-109">[in] Maximální velikost `rMethods` pole.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4a5e6-110">[out] Počet tokenů MemberDef vrácené v `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a5e6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4a5e6-111">Return Value</span></span>  
  
|<span data-ttu-id="4a5e6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a5e6-112">HRESULT</span></span>|<span data-ttu-id="4a5e6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4a5e6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4a5e6-114">`EnumUnresolvedMethods` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4a5e6-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4a5e6-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a5e6-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a5e6-117">Remarks</span></span>  
 <span data-ttu-id="4a5e6-118">Nerozpoznaná metoda je ten, který byl deklarován, ale není implementován.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="4a5e6-119">Metodu je zahrnutá ve výčtu, pokud metoda je označena jako `miForwardRef` a buď `mdPinvokeImpl` nebo `miRuntime` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="4a5e6-120">Jinými slovy, nerozpoznaná metoda je metoda třídy, která je označena `miForwardRef` , ale které není implementovaná v nespravovaném kódu (kontaktovat prostřednictvím PInvoke) ani implementována interně modulem samotný modul runtime</span><span class="sxs-lookup"><span data-stu-id="4a5e6-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="4a5e6-121">Výčet vyloučí všechny metody, které jsou definovány v oboru modulu (globals) nebo v rozhraní nebo abstraktní.</span><span class="sxs-lookup"><span data-stu-id="4a5e6-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a5e6-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a5e6-122">Requirements</span></span>  
 <span data-ttu-id="4a5e6-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a5e6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a5e6-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a5e6-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a5e6-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a5e6-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a5e6-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a5e6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5e6-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a5e6-127">See also</span></span>
- [<span data-ttu-id="4a5e6-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a5e6-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4a5e6-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a5e6-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
