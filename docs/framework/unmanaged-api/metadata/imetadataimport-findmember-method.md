---
title: IMetaDataImport::FindMember – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503676"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="150ab-102">IMetaDataImport::FindMember – metoda</span><span class="sxs-lookup"><span data-stu-id="150ab-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="150ab-103">Získá ukazatel na token memberDef či pole nebo metody, které jsou uzavřeny zadaným <xref:System.Type> a mají zadaný název a signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="150ab-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="150ab-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="150ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="150ab-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="150ab-106">pro Token TypeDef pro třídu nebo rozhraní, který obklopuje člena, který se má vyhledat.</span><span class="sxs-lookup"><span data-stu-id="150ab-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="150ab-107">Pokud je tato hodnota `mdTokenNil` , vyhledávání je provedeno pro globální proměnnou nebo globální funkci.</span><span class="sxs-lookup"><span data-stu-id="150ab-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="150ab-108">pro Název hledaného člena.</span><span class="sxs-lookup"><span data-stu-id="150ab-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="150ab-109">pro Ukazatel na binární podpis metadat člena.</span><span class="sxs-lookup"><span data-stu-id="150ab-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="150ab-110">pro Velikost v bajtech `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="150ab-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="150ab-111">mimo Ukazatel na odpovídajícího tokenu memberDef či.</span><span class="sxs-lookup"><span data-stu-id="150ab-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="150ab-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="150ab-112">Remarks</span></span>  
 <span data-ttu-id="150ab-113">Určíte člena pomocí své nadřazené třídy nebo rozhraní ( `td` ), jeho název ( `szName` ) a volitelně jeho signatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="150ab-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="150ab-114">Třída nebo rozhraní může obsahovat více členů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="150ab-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="150ab-115">V takovém případě předejte signaturu člena, aby našli jedinečnou shodu.</span><span class="sxs-lookup"><span data-stu-id="150ab-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="150ab-116">Signatura předaná do `FindMember` musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor.</span><span class="sxs-lookup"><span data-stu-id="150ab-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="150ab-117">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="150ab-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="150ab-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="150ab-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="150ab-119">Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít ho jako vstup pro vstup do `FindMember` .</span><span class="sxs-lookup"><span data-stu-id="150ab-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="150ab-120">`FindMember`Vyhledá pouze členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="150ab-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="150ab-121">`FindMember`je pomocná metoda.</span><span class="sxs-lookup"><span data-stu-id="150ab-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="150ab-122">Volá [IMetaDataImport:: FindMethod –](imetadataimport-findmethod-method.md);. Pokud toto volání nenajde shodu, `FindMember` pak zavolá [IMetaDataImport:: findfield –](imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="150ab-122">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="150ab-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="150ab-123">Requirements</span></span>  
 <span data-ttu-id="150ab-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="150ab-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="150ab-125">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="150ab-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="150ab-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="150ab-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="150ab-127">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="150ab-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="150ab-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="150ab-128">See also</span></span>

- [<span data-ttu-id="150ab-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="150ab-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="150ab-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="150ab-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
