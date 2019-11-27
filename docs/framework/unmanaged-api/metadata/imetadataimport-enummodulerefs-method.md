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
ms.openlocfilehash: 66186d25e8fee0d6b25c0a2069d46ff9a104c625
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450029"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="db2ca-102">IMetaDataImport::EnumModuleRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="db2ca-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="db2ca-103">Vytvoří výčet tokenů Odkaz ModuleRef, které reprezentují importované moduly.</span><span class="sxs-lookup"><span data-stu-id="db2ca-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db2ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db2ca-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db2ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db2ca-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="db2ca-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="db2ca-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="db2ca-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="db2ca-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="db2ca-108">mimo Pole, které se používá k uložení tokenů Odkaz ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="db2ca-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="db2ca-109">pro Maximální velikost `rModuleRefs` pole</span><span class="sxs-lookup"><span data-stu-id="db2ca-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="db2ca-110">mimo Počet tokenů Odkaz ModuleRef vrácených v `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="db2ca-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db2ca-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db2ca-111">Return Value</span></span>  
  
|<span data-ttu-id="db2ca-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db2ca-112">HRESULT</span></span>|<span data-ttu-id="db2ca-113">Popis</span><span class="sxs-lookup"><span data-stu-id="db2ca-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="db2ca-114">`EnumModuleRefs` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="db2ca-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="db2ca-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="db2ca-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="db2ca-116">V takovém případě je `pcModuleRefs` nula.</span><span class="sxs-lookup"><span data-stu-id="db2ca-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db2ca-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db2ca-117">Requirements</span></span>  
 <span data-ttu-id="db2ca-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db2ca-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db2ca-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="db2ca-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db2ca-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db2ca-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db2ca-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db2ca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2ca-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db2ca-122">See also</span></span>

- [<span data-ttu-id="db2ca-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db2ca-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="db2ca-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db2ca-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
