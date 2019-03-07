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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb38c61e8dbd29a0ff87165b5daf49e733b34047
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466541"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="cae28-102">IMetaDataImport::GetInterfaceImplProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cae28-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="cae28-103">Získá ukazatel na tokeny metadat pro <xref:System.Type> zadanou metodu, která implementuje a rozhraní, která deklaruje dané metody.</span><span class="sxs-lookup"><span data-stu-id="cae28-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="cae28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cae28-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cae28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cae28-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="cae28-106">[in] Představující metodu vrátit třídu a interface tokeny pro token metadat.</span><span class="sxs-lookup"><span data-stu-id="cae28-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cae28-107">[out] Token metadat představující třídu, která implementuje metodu.</span><span class="sxs-lookup"><span data-stu-id="cae28-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="cae28-108">[out] Představuje rozhraní, které definuje implementované metody token metadat.</span><span class="sxs-lookup"><span data-stu-id="cae28-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="cae28-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cae28-109">Remarks</span></span>

 <span data-ttu-id="cae28-110">Získat hodnotu pro `iImpl` voláním [enuminterfaceimpls –](imetadataimport-enuminterfaceimpls-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cae28-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>
 
 <span data-ttu-id="cae28-111">Předpokládejme například, že třída má `mdTypeDef` token hodnota 0x02000007 a implementuje tři rozhraní, jejichž typy mají tokeny:</span><span class="sxs-lookup"><span data-stu-id="cae28-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span> 

- <span data-ttu-id="cae28-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="cae28-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="cae28-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="cae28-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="cae28-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="cae28-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="cae28-115">Obecně tyto informace jsou uloženy do tabulky implementace rozhraní jako:</span><span class="sxs-lookup"><span data-stu-id="cae28-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="cae28-116">Číslo řádku</span><span class="sxs-lookup"><span data-stu-id="cae28-116">Row number</span></span> | <span data-ttu-id="cae28-117">Token třídy</span><span class="sxs-lookup"><span data-stu-id="cae28-117">Class token</span></span> | <span data-ttu-id="cae28-118">Token rozhraní</span><span class="sxs-lookup"><span data-stu-id="cae28-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="cae28-119">4</span><span class="sxs-lookup"><span data-stu-id="cae28-119">4</span></span>          |             |                 |
| <span data-ttu-id="cae28-120">5</span><span class="sxs-lookup"><span data-stu-id="cae28-120">5</span></span>          | <span data-ttu-id="cae28-121">02000007</span><span class="sxs-lookup"><span data-stu-id="cae28-121">02000007</span></span>    | <span data-ttu-id="cae28-122">02000003</span><span class="sxs-lookup"><span data-stu-id="cae28-122">02000003</span></span>        |
| <span data-ttu-id="cae28-123">6</span><span class="sxs-lookup"><span data-stu-id="cae28-123">6</span></span>          | <span data-ttu-id="cae28-124">02000007</span><span class="sxs-lookup"><span data-stu-id="cae28-124">02000007</span></span>    | <span data-ttu-id="cae28-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="cae28-125">0100000A</span></span>        |
| <span data-ttu-id="cae28-126">7</span><span class="sxs-lookup"><span data-stu-id="cae28-126">7</span></span>          |             |                 |
| <span data-ttu-id="cae28-127">8</span><span class="sxs-lookup"><span data-stu-id="cae28-127">8</span></span>          | <span data-ttu-id="cae28-128">02000007</span><span class="sxs-lookup"><span data-stu-id="cae28-128">02000007</span></span>    | <span data-ttu-id="cae28-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="cae28-129">0200001C</span></span>        |

<span data-ttu-id="cae28-130">Odvolat token, který je 4 bajty. hodnota:</span><span class="sxs-lookup"><span data-stu-id="cae28-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="cae28-131">Nižší 3 bajtů obsahovat číslo řádku, nebo identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="cae28-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="cae28-132">Horní bajtů obsahuje typ tokenu – 0x09 pro `mdtInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="cae28-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="cae28-133">`GetInterfaceImplProps` Vrátí informace uchovávané v řádku, jehož token, který zadáte v `iImpl` argument.</span><span class="sxs-lookup"><span data-stu-id="cae28-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="cae28-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cae28-134">Requirements</span></span>  
 <span data-ttu-id="cae28-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae28-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae28-136">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cae28-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cae28-137">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cae28-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cae28-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae28-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae28-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cae28-139">See also</span></span>
- [<span data-ttu-id="cae28-140">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cae28-140">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cae28-141">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cae28-141">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
