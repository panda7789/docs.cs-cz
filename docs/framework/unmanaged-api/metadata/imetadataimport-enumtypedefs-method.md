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
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177287"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="90ea9-102">IMetaDataImport::EnumTypeDefs – metoda</span><span class="sxs-lookup"><span data-stu-id="90ea9-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="90ea9-103">Výčet TypeDef tokeny představující všechny typy v rámci aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="90ea9-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ea9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90ea9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90ea9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90ea9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="90ea9-106">[out] Ukazatel na nový čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="90ea9-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="90ea9-107">To musí být NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="90ea9-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="90ea9-108">[v] Pole používané k ukládání tokenů TypeDef.</span><span class="sxs-lookup"><span data-stu-id="90ea9-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="90ea9-109">[v] Maximální velikost `rTypeDefs` pole.</span><span class="sxs-lookup"><span data-stu-id="90ea9-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="90ea9-110">[out] Počet tokenů TypeDef vrácených v `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="90ea9-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90ea9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90ea9-111">Return Value</span></span>  
  
|<span data-ttu-id="90ea9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90ea9-112">HRESULT</span></span>|<span data-ttu-id="90ea9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="90ea9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="90ea9-114">`EnumTypeDefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="90ea9-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="90ea9-115">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="90ea9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="90ea9-116">V tom `pcTypeDefs` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="90ea9-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90ea9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90ea9-117">Remarks</span></span>  
 <span data-ttu-id="90ea9-118">TypeDef token představuje typ, jako je například třída nebo rozhraní, stejně jako jakýkoli typ přidán prostřednictvím mechanismu rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="90ea9-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ea9-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90ea9-119">Requirements</span></span>  
 <span data-ttu-id="90ea9-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ea9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ea9-121">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="90ea9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90ea9-122">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90ea9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90ea9-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ea9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ea9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="90ea9-124">See also</span></span>

- [<span data-ttu-id="90ea9-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ea9-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="90ea9-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90ea9-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
