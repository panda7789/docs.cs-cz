---
title: IMetaDataImport::FindMemberRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 068014732cee91147edaec29fa0f954a741d8b5c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491651"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="d2464-102">IMetaDataImport::FindMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="d2464-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="d2464-103">Získá ukazatel na token MemberRef pro odkaz na člena, který je uzavřený zadaným <xref:System.Type> a má zadaný název a signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="d2464-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2464-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2464-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2464-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2464-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d2464-106">pro Token TypeRef pro třídu nebo rozhraní, které obklopují odkaz na člena pro hledání.</span><span class="sxs-lookup"><span data-stu-id="d2464-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="d2464-107">Pokud je tato hodnota `mdTokenNil` , vyhledávání je provedeno pro globální proměnnou nebo odkaz globální funkce.</span><span class="sxs-lookup"><span data-stu-id="d2464-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="d2464-108">pro Název odkazu na člena, který se má vyhledat</span><span class="sxs-lookup"><span data-stu-id="d2464-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d2464-109">pro Ukazatel na binární podpis metadat odkazu na člena.</span><span class="sxs-lookup"><span data-stu-id="d2464-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d2464-110">pro Velikost v bajtech `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d2464-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="d2464-111">mimo Ukazatel na shodný token MemberRef.</span><span class="sxs-lookup"><span data-stu-id="d2464-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2464-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2464-112">Remarks</span></span>  
 <span data-ttu-id="d2464-113">Určíte člena pomocí své nadřazené třídy nebo rozhraní ( `td` ), jeho název ( `szName` ) a volitelně jeho signatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="d2464-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="d2464-114">Signatura předaná do `FindMemberRef` musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor.</span><span class="sxs-lookup"><span data-stu-id="d2464-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d2464-115">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d2464-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d2464-116">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="d2464-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="d2464-117">Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup do `FindMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="d2464-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="d2464-118">`FindMemberRef`Vyhledá pouze odkazy na členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné odkazy členů.</span><span class="sxs-lookup"><span data-stu-id="d2464-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2464-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2464-119">Requirements</span></span>  
 <span data-ttu-id="d2464-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2464-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2464-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d2464-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2464-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2464-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2464-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2464-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2464-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2464-124">See also</span></span>

- [<span data-ttu-id="d2464-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2464-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d2464-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2464-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
