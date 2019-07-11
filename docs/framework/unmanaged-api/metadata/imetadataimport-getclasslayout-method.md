---
title: IMetaDataImport::GetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6094bbedcc5386d3f5c0400960e47ac91defe2a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782445"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="dd3db-102">IMetaDataImport::GetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="dd3db-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="dd3db-103">Získá informace o rozložení třídy odkazuje zadaný TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="dd3db-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd3db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd3db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd3db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd3db-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dd3db-106">[in] Token TypeDef pro třídu s rozložením se vraťte.</span><span class="sxs-lookup"><span data-stu-id="dd3db-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="dd3db-107">[out] Jedna z hodnot 1, 2, 4, 8 nebo 16, představující velikosti balíčku třídy.</span><span class="sxs-lookup"><span data-stu-id="dd3db-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="dd3db-108">[out] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dd3db-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dd3db-109">[in] Maximální velikost `rFieldOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="dd3db-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="dd3db-110">[out] Počet prvků vrácených v `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="dd3db-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="dd3db-111">[out] Velikost v bajtech třída představovaná typem `td`.</span><span class="sxs-lookup"><span data-stu-id="dd3db-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd3db-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd3db-112">Requirements</span></span>  
 <span data-ttu-id="dd3db-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd3db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd3db-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd3db-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd3db-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd3db-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd3db-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd3db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3db-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd3db-117">See also</span></span>

- [<span data-ttu-id="dd3db-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd3db-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dd3db-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd3db-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
