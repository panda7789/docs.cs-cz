---
title: "IMetaDataImport::EnumTypeDefs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aeb0e3c2eab4cde219b050bcf0e50202fe2be3f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="aa79d-102">IMetaDataImport::EnumTypeDefs – metoda</span><span class="sxs-lookup"><span data-stu-id="aa79d-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="aa79d-103">Vytvoří výčet TypeDef tokeny představující všechny typy v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="aa79d-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa79d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa79d-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa79d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa79d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="aa79d-106">[out] Ukazatel na nové enumerátor.</span><span class="sxs-lookup"><span data-stu-id="aa79d-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="aa79d-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="aa79d-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="aa79d-108">[v] Pole používá k ukládání TypeDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="aa79d-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="aa79d-109">[v] Maximální velikost `rTypeDefs` pole.</span><span class="sxs-lookup"><span data-stu-id="aa79d-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="aa79d-110">[out] Počet TypeDef tokeny, vrátí se v `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="aa79d-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa79d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa79d-111">Return Value</span></span>  
  
|<span data-ttu-id="aa79d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa79d-112">HRESULT</span></span>|<span data-ttu-id="aa79d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="aa79d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aa79d-114">`EnumTypeDefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="aa79d-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="aa79d-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="aa79d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="aa79d-116">V takovém případě `pcTypeDefs` je nulová.</span><span class="sxs-lookup"><span data-stu-id="aa79d-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa79d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa79d-117">Remarks</span></span>  
 <span data-ttu-id="aa79d-118">TypeDef token představuje typu například třídy nebo rozhraní, stejně jako jakýkoli typ přidané prostřednictvím mechanismus rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="aa79d-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa79d-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa79d-119">Requirements</span></span>  
 <span data-ttu-id="aa79d-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa79d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa79d-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa79d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa79d-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa79d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa79d-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa79d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa79d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa79d-124">See Also</span></span>  
 [<span data-ttu-id="aa79d-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa79d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="aa79d-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa79d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
