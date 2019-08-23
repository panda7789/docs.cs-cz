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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4eefb7ec1e7d0d130ec64531a59d1d5bbce04963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968922"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="f1e14-102">IMetaDataImport::FindMember – metoda</span><span class="sxs-lookup"><span data-stu-id="f1e14-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="f1e14-103">Získá ukazatel na token memberDef či pole nebo metody, které jsou uzavřeny zadaným <xref:System.Type> a mají zadaný název a signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="f1e14-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1e14-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1e14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1e14-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f1e14-106">pro Token TypeDef pro třídu nebo rozhraní, který obklopuje člena, který se má vyhledat.</span><span class="sxs-lookup"><span data-stu-id="f1e14-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="f1e14-107">Pokud je `mdTokenNil`tato hodnota, vyhledávání je provedeno pro globální proměnnou nebo globální funkci.</span><span class="sxs-lookup"><span data-stu-id="f1e14-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="f1e14-108">pro Název hledaného člena.</span><span class="sxs-lookup"><span data-stu-id="f1e14-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="f1e14-109">pro Ukazatel na binární podpis metadat člena.</span><span class="sxs-lookup"><span data-stu-id="f1e14-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="f1e14-110">pro Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f1e14-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="f1e14-111">mimo Ukazatel na odpovídajícího tokenu memberDef či.</span><span class="sxs-lookup"><span data-stu-id="f1e14-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1e14-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1e14-112">Remarks</span></span>  
 <span data-ttu-id="f1e14-113">Určíte člena pomocí své nadřazené třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho signatura (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="f1e14-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="f1e14-114">Třída nebo rozhraní může obsahovat více členů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="f1e14-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="f1e14-115">V takovém případě předejte signaturu člena, aby našli jedinečnou shodu.</span><span class="sxs-lookup"><span data-stu-id="f1e14-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="f1e14-116">Signatura předaná `FindMember` do musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor.</span><span class="sxs-lookup"><span data-stu-id="f1e14-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="f1e14-117">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f1e14-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="f1e14-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="f1e14-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="f1e14-119">Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít ho jako vstup pro vstup do `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="f1e14-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="f1e14-120">`FindMember`Vyhledá pouze členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="f1e14-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1e14-121">`FindMember`je pomocná metoda.</span><span class="sxs-lookup"><span data-stu-id="f1e14-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="f1e14-122">Volá [IMetaDataImport:: FindMethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md);. Pokud toto volání nenajde shodu, `FindMember` pak zavolá [IMetaDataImport:: findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="f1e14-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e14-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1e14-123">Requirements</span></span>  
 <span data-ttu-id="f1e14-124">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1e14-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1e14-125">**Hlaviček** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f1e14-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1e14-126">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1e14-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1e14-127">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e14-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e14-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1e14-128">See also</span></span>

- [<span data-ttu-id="f1e14-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1e14-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f1e14-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1e14-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
