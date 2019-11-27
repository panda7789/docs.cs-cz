---
title: IMetaDataImport::EnumCustomAttributes – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: a43c1883038e41cac1b58c78bc26f20d436ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440235"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="63d76-102">IMetaDataImport::EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="63d76-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="63d76-103">Vytvoří výčet tokenů definice vlastního atributu přidružených k zadanému typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="63d76-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63d76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63d76-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63d76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63d76-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="63d76-106">[in, out] Ukazatel na vrácený enumerátor.</span><span class="sxs-lookup"><span data-stu-id="63d76-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="63d76-107">pro Token pro rozsah výčtu nebo nula pro všechny vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="63d76-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="63d76-108">pro Token pro konstruktor typu atributů, které mají být vyčísleny, nebo `null` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="63d76-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="63d76-109">mimo Pole tokenů vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="63d76-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="63d76-110">pro Maximální velikost `rCustomAttributes` pole</span><span class="sxs-lookup"><span data-stu-id="63d76-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="63d76-111">[out, volitelné] Skutečný počet hodnot tokenu vrácených v `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="63d76-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63d76-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="63d76-112">Return Value</span></span>  
  
|<span data-ttu-id="63d76-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63d76-113">HRESULT</span></span>|<span data-ttu-id="63d76-114">Popis</span><span class="sxs-lookup"><span data-stu-id="63d76-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="63d76-115">`EnumCustomAttributes` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="63d76-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="63d76-116">Neexistují žádné vlastní atributy k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="63d76-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="63d76-117">V takovém případě je `pcCustomAttributes` nula.</span><span class="sxs-lookup"><span data-stu-id="63d76-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63d76-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63d76-118">Requirements</span></span>  
 <span data-ttu-id="63d76-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63d76-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d76-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="63d76-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63d76-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63d76-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63d76-122">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d76-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d76-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63d76-123">See also</span></span>

- [<span data-ttu-id="63d76-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63d76-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="63d76-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63d76-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
