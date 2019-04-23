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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b80bb7b62d3a4ffee61cc6756b7d7d02f2b074bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196200"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="8c778-102">IMetaDataImport::EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="8c778-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="8c778-103">Vytvoří výčet vlastní definice atributu tokeny přidružené zadaný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="8c778-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c778-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c778-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c778-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c778-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8c778-106">[out v] Ukazatel na vrácený enumerátor.</span><span class="sxs-lookup"><span data-stu-id="8c778-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="8c778-107">[in] Token pro rozsah výčtu nebo nulu pro všechny vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="8c778-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8c778-108">[in] Token pro konstruktor typu atributů pro provedení výčtu nebo `null` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="8c778-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="8c778-109">[out] Pole vlastních atributů tokeny.</span><span class="sxs-lookup"><span data-stu-id="8c778-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8c778-110">[in] Maximální velikost `rCustomAttributes` pole.</span><span class="sxs-lookup"><span data-stu-id="8c778-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="8c778-111">[out, volitelné] Skutečný počet tokenů hodnot vrácených v `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="8c778-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c778-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c778-112">Return Value</span></span>  
  
|<span data-ttu-id="8c778-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c778-113">HRESULT</span></span>|<span data-ttu-id="8c778-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8c778-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8c778-115">`EnumCustomAttributes` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8c778-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8c778-116">Neexistují žádné vlastní atributy k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="8c778-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="8c778-117">V takovém případě `pcCustomAttributes` je nula.</span><span class="sxs-lookup"><span data-stu-id="8c778-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c778-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c778-118">Requirements</span></span>  
 <span data-ttu-id="8c778-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c778-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c778-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c778-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c778-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c778-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c778-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c778-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c778-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c778-123">See also</span></span>

- [<span data-ttu-id="8c778-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c778-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8c778-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c778-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
