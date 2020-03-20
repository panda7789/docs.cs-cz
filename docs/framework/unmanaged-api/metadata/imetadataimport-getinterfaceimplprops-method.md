---
title: IMetaDataImport::GetInterfaceImplProps – metoda
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 4b8ddf7fec12d175f030c0ea0ed982c6fb334aee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175379"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="38568-102">IMetaDataImport::GetInterfaceImplProps – metoda</span><span class="sxs-lookup"><span data-stu-id="38568-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="38568-103">Získá ukazatel na tokeny metadat <xref:System.Type> pro, který implementuje zadanou metodu a pro rozhraní, které deklaruje tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="38568-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="38568-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38568-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38568-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38568-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="38568-106">[v] Token metadat představující metodu vrátit tokeny třídy a rozhraní pro.</span><span class="sxs-lookup"><span data-stu-id="38568-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="38568-107">[out] Token metadat představující třídu, která implementuje metodu.</span><span class="sxs-lookup"><span data-stu-id="38568-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="38568-108">[out] Token metadat představující rozhraní, které definuje implementovanou metodu.</span><span class="sxs-lookup"><span data-stu-id="38568-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="38568-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38568-109">Remarks</span></span>

 <span data-ttu-id="38568-110">Hodnotu získáte `iImpl` voláním metody [EnumInterfaceImpls.](imetadataimport-enuminterfaceimpls-method.md)</span><span class="sxs-lookup"><span data-stu-id="38568-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="38568-111">Předpokládejme například, že `mdTypeDef` třída má hodnotu tokenu 0x02000007 a že implementuje tři rozhraní, jejichž typy mají tokeny:</span><span class="sxs-lookup"><span data-stu-id="38568-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="38568-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="38568-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="38568-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="38568-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="38568-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="38568-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="38568-115">Koncepčně jsou tyto informace uloženy do tabulky implementace rozhraní jako:</span><span class="sxs-lookup"><span data-stu-id="38568-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="38568-116">Číslo řádku</span><span class="sxs-lookup"><span data-stu-id="38568-116">Row number</span></span> | <span data-ttu-id="38568-117">Token třídy</span><span class="sxs-lookup"><span data-stu-id="38568-117">Class token</span></span> | <span data-ttu-id="38568-118">Token rozhraní</span><span class="sxs-lookup"><span data-stu-id="38568-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="38568-119">4</span><span class="sxs-lookup"><span data-stu-id="38568-119">4</span></span>          |             |                 |
| <span data-ttu-id="38568-120">5</span><span class="sxs-lookup"><span data-stu-id="38568-120">5</span></span>          | <span data-ttu-id="38568-121">02000007</span><span class="sxs-lookup"><span data-stu-id="38568-121">02000007</span></span>    | <span data-ttu-id="38568-122">02000003</span><span class="sxs-lookup"><span data-stu-id="38568-122">02000003</span></span>        |
| <span data-ttu-id="38568-123">6</span><span class="sxs-lookup"><span data-stu-id="38568-123">6</span></span>          | <span data-ttu-id="38568-124">02000007</span><span class="sxs-lookup"><span data-stu-id="38568-124">02000007</span></span>    | <span data-ttu-id="38568-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="38568-125">0100000A</span></span>        |
| <span data-ttu-id="38568-126">7</span><span class="sxs-lookup"><span data-stu-id="38568-126">7</span></span>          |             |                 |
| <span data-ttu-id="38568-127">8</span><span class="sxs-lookup"><span data-stu-id="38568-127">8</span></span>          | <span data-ttu-id="38568-128">02000007</span><span class="sxs-lookup"><span data-stu-id="38568-128">02000007</span></span>    | <span data-ttu-id="38568-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="38568-129">0200001C</span></span>        |

<span data-ttu-id="38568-130">Odvolání, token je 4bajtová hodnota:</span><span class="sxs-lookup"><span data-stu-id="38568-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="38568-131">Dolní 3 bajty drží číslo řádku nebo RID.</span><span class="sxs-lookup"><span data-stu-id="38568-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="38568-132">Horní bajt obsahuje typ tokenu – `mdtInterfaceImpl`0x09 pro .</span><span class="sxs-lookup"><span data-stu-id="38568-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="38568-133">`GetInterfaceImplProps`vrátí informace držené v řádku, jehož `iImpl` token zadáte v argumentu.</span><span class="sxs-lookup"><span data-stu-id="38568-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="38568-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38568-134">Requirements</span></span>  
 <span data-ttu-id="38568-135">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38568-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38568-136">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="38568-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38568-137">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38568-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38568-138">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38568-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38568-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="38568-139">See also</span></span>

- [<span data-ttu-id="38568-140">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38568-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="38568-141">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38568-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
