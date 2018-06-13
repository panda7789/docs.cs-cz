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
ms.openlocfilehash: 294156983507476b7ddfda3bc3cad16bb32f422b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445406"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="14a2f-102">IMetaDataImport::EnumModuleRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="14a2f-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="14a2f-103">Vytvoří výčet Odkaz ModuleRef tokeny, které představují importovaných modulů.</span><span class="sxs-lookup"><span data-stu-id="14a2f-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14a2f-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14a2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14a2f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="14a2f-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="14a2f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="14a2f-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="14a2f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="14a2f-108">[out] Pole používá k ukládání Odkaz ModuleRef tokenů.</span><span class="sxs-lookup"><span data-stu-id="14a2f-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="14a2f-109">[v] Maximální velikost `rModuleRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="14a2f-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="14a2f-110">[out] Počet Odkaz ModuleRef tokeny, vrátí se v `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="14a2f-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14a2f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="14a2f-111">Return Value</span></span>  
  
|<span data-ttu-id="14a2f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14a2f-112">HRESULT</span></span>|<span data-ttu-id="14a2f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="14a2f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="14a2f-114">`EnumModuleRefs` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="14a2f-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="14a2f-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="14a2f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="14a2f-116">V takovém případě `pcModuleRefs` je nulová.</span><span class="sxs-lookup"><span data-stu-id="14a2f-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14a2f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14a2f-117">Requirements</span></span>  
 <span data-ttu-id="14a2f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a2f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a2f-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14a2f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14a2f-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14a2f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14a2f-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a2f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a2f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="14a2f-122">See Also</span></span>  
 [<span data-ttu-id="14a2f-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14a2f-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="14a2f-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14a2f-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
