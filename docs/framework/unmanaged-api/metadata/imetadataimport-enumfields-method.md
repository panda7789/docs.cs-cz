---
title: IMetaDataImport::EnumFields – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 2d32dc8ae59fc1a4a189d849437cc95ea3b94a4d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449535"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="a679b-102">IMetaDataImport::EnumFields – metoda</span><span class="sxs-lookup"><span data-stu-id="a679b-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="a679b-103">Vytvoří výčet tokenů FieldDef pro typ, na který odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a679b-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a679b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a679b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a679b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a679b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a679b-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="a679b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="a679b-107">pro Token TypeDef třídy, jejíž pole mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="a679b-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="a679b-108">mimo Seznam tokenů FieldDef.</span><span class="sxs-lookup"><span data-stu-id="a679b-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a679b-109">pro Maximální velikost `rFields` pole</span><span class="sxs-lookup"><span data-stu-id="a679b-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a679b-110">mimo Skutečný počet FieldDef tokenů vrácených v `rFields`.</span><span class="sxs-lookup"><span data-stu-id="a679b-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a679b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a679b-111">Return Value</span></span>  
  
|<span data-ttu-id="a679b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a679b-112">HRESULT</span></span>|<span data-ttu-id="a679b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a679b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a679b-114">`EnumFields` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a679b-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a679b-115">Neexistují žádná pole k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="a679b-115">There are no fields to enumerate.</span></span> <span data-ttu-id="a679b-116">V takovém případě je `pcTokens` nula.</span><span class="sxs-lookup"><span data-stu-id="a679b-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a679b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a679b-117">Requirements</span></span>  
 <span data-ttu-id="a679b-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a679b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a679b-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a679b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a679b-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a679b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a679b-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a679b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a679b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a679b-122">See also</span></span>

- [<span data-ttu-id="a679b-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a679b-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a679b-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a679b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
