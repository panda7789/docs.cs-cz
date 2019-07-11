---
title: IMetaDataImport::EnumModuleRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afa2d35a193a11360b52bcbdc1d9e5dae16d1c90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782128"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="c6784-102">IMetaDataImport::EnumModuleRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="c6784-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="c6784-103">Vytvoří výčet Odkaz ModuleRef tokeny, které představují importované moduly.</span><span class="sxs-lookup"><span data-stu-id="c6784-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6784-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6784-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6784-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6784-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c6784-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c6784-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c6784-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="c6784-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="c6784-108">[out] Pole pro ukládání tokenů Odkaz ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="c6784-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c6784-109">[in] Maximální velikost `rModuleRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="c6784-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="c6784-110">[out] Počet tokenů Odkaz ModuleRef vrácené v `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="c6784-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6784-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6784-111">Return Value</span></span>  
  
|<span data-ttu-id="c6784-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6784-112">HRESULT</span></span>|<span data-ttu-id="c6784-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c6784-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c6784-114">`EnumModuleRefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c6784-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c6784-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="c6784-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c6784-116">V takovém případě `pcModuleRefs` je nula.</span><span class="sxs-lookup"><span data-stu-id="c6784-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6784-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6784-117">Requirements</span></span>  
 <span data-ttu-id="c6784-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6784-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6784-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6784-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6784-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6784-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6784-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6784-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6784-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6784-122">See also</span></span>

- [<span data-ttu-id="c6784-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6784-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c6784-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6784-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
