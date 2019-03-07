---
title: IMetaDataImport::EnumTypeDefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a285543571c843a982b6615fdc4b5f1325ed066
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466957"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="22f95-102">IMetaDataImport::EnumTypeDefs – metoda</span><span class="sxs-lookup"><span data-stu-id="22f95-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="22f95-103">Vytvoří výčet TypeDef tokeny představující všechny typy v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="22f95-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22f95-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22f95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22f95-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="22f95-106">[out] Ukazatel na nový čítač.</span><span class="sxs-lookup"><span data-stu-id="22f95-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="22f95-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="22f95-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="22f95-108">[in] Pole pro ukládání tokenů TypeDef.</span><span class="sxs-lookup"><span data-stu-id="22f95-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="22f95-109">[in] Maximální velikost `rTypeDefs` pole.</span><span class="sxs-lookup"><span data-stu-id="22f95-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="22f95-110">[out] Počet tokenů TypeDef vrácené v `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="22f95-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22f95-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22f95-111">Return Value</span></span>  
  
|<span data-ttu-id="22f95-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22f95-112">HRESULT</span></span>|<span data-ttu-id="22f95-113">Popis</span><span class="sxs-lookup"><span data-stu-id="22f95-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="22f95-114">`EnumTypeDefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="22f95-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="22f95-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="22f95-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="22f95-116">V takovém případě `pcTypeDefs` je nula.</span><span class="sxs-lookup"><span data-stu-id="22f95-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f95-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22f95-117">Remarks</span></span>  
 <span data-ttu-id="22f95-118">TypeDef token představuje typ, například třídy nebo rozhraní, stejně jako libovolný typ přidány prostřednictvím mechanismem rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="22f95-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f95-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22f95-119">Requirements</span></span>  
 <span data-ttu-id="22f95-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22f95-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f95-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22f95-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22f95-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22f95-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22f95-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22f95-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f95-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22f95-124">See also</span></span>
- [<span data-ttu-id="22f95-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22f95-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="22f95-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22f95-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
