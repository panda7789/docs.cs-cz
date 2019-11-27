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
ms.openlocfilehash: e5eb735acac73d694a0719c206bd22711a8c0333
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437548"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="4b84c-102">IMetaDataImport::GetInterfaceImplProps – metoda</span><span class="sxs-lookup"><span data-stu-id="4b84c-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="4b84c-103">Získá ukazatel na tokeny metadat pro <xref:System.Type>, které implementují zadanou metodu, a pro rozhraní, které deklaruje tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="4b84c-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="4b84c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b84c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b84c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b84c-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="4b84c-106">pro Token metadat představující metodu pro návrat třídy a tokeny rozhraní pro.</span><span class="sxs-lookup"><span data-stu-id="4b84c-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="4b84c-107">mimo Token metadat představující třídu, která implementuje metodu.</span><span class="sxs-lookup"><span data-stu-id="4b84c-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="4b84c-108">mimo Token metadat představující rozhraní, které definuje implementovanou metodu.</span><span class="sxs-lookup"><span data-stu-id="4b84c-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="4b84c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b84c-109">Remarks</span></span>

 <span data-ttu-id="4b84c-110">Hodnotu pro `iImpl` získáte zavoláním metody [enuminterfaceimpls –](imetadataimport-enuminterfaceimpls-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4b84c-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="4b84c-111">Předpokládejme například, že třída má hodnotu `mdTypeDef` tokenu 0x02000007 a že implementuje tři rozhraní, jejichž typy mají tokeny:</span><span class="sxs-lookup"><span data-stu-id="4b84c-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="4b84c-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="4b84c-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="4b84c-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="4b84c-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="4b84c-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="4b84c-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="4b84c-115">V koncepčních případech jsou tyto informace uloženy do tabulky implementace rozhraní jako:</span><span class="sxs-lookup"><span data-stu-id="4b84c-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="4b84c-116">Číslo řádku</span><span class="sxs-lookup"><span data-stu-id="4b84c-116">Row number</span></span> | <span data-ttu-id="4b84c-117">Token třídy</span><span class="sxs-lookup"><span data-stu-id="4b84c-117">Class token</span></span> | <span data-ttu-id="4b84c-118">Token rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b84c-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="4b84c-119">4</span><span class="sxs-lookup"><span data-stu-id="4b84c-119">4</span></span>          |             |                 |
| <span data-ttu-id="4b84c-120">5</span><span class="sxs-lookup"><span data-stu-id="4b84c-120">5</span></span>          | <span data-ttu-id="4b84c-121">02000007</span><span class="sxs-lookup"><span data-stu-id="4b84c-121">02000007</span></span>    | <span data-ttu-id="4b84c-122">02000003</span><span class="sxs-lookup"><span data-stu-id="4b84c-122">02000003</span></span>        |
| <span data-ttu-id="4b84c-123">6</span><span class="sxs-lookup"><span data-stu-id="4b84c-123">6</span></span>          | <span data-ttu-id="4b84c-124">02000007</span><span class="sxs-lookup"><span data-stu-id="4b84c-124">02000007</span></span>    | <span data-ttu-id="4b84c-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="4b84c-125">0100000A</span></span>        |
| <span data-ttu-id="4b84c-126">7</span><span class="sxs-lookup"><span data-stu-id="4b84c-126">7</span></span>          |             |                 |
| <span data-ttu-id="4b84c-127">8</span><span class="sxs-lookup"><span data-stu-id="4b84c-127">8</span></span>          | <span data-ttu-id="4b84c-128">02000007</span><span class="sxs-lookup"><span data-stu-id="4b84c-128">02000007</span></span>    | <span data-ttu-id="4b84c-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="4b84c-129">0200001C</span></span>        |

<span data-ttu-id="4b84c-130">Odvolání tokenu je hodnota o velikosti 4 bajty:</span><span class="sxs-lookup"><span data-stu-id="4b84c-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="4b84c-131">Dolní 3 bajty obsahují číslo řádku nebo identifikátor RID.</span><span class="sxs-lookup"><span data-stu-id="4b84c-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="4b84c-132">Horní bajt obsahuje typ tokenu – 0x09 pro `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="4b84c-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="4b84c-133">`GetInterfaceImplProps` vrátí informace uchovávané v řádku, jehož token zadáte v argumentu `iImpl`.</span><span class="sxs-lookup"><span data-stu-id="4b84c-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="4b84c-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b84c-134">Requirements</span></span>  
 <span data-ttu-id="4b84c-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b84c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b84c-136">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4b84c-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b84c-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b84c-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b84c-138">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b84c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b84c-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b84c-139">See also</span></span>

- [<span data-ttu-id="4b84c-140">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b84c-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4b84c-141">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b84c-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
