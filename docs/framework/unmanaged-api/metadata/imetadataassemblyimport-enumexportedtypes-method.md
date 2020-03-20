---
title: IMetaDataAssemblyImport::EnumExportedTypes – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176003"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="78f0b-102">IMetaDataAssemblyImport::EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="78f0b-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="78f0b-103">Vyjmenovává exportované typy odkazované v manifestu sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="78f0b-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78f0b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78f0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78f0b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="78f0b-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="78f0b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="78f0b-107">To musí být hodnota `EnumExportedTypes` null při první volání metody.</span><span class="sxs-lookup"><span data-stu-id="78f0b-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="78f0b-108">[out] Výčet tokenů `mdExportedType` metadat.</span><span class="sxs-lookup"><span data-stu-id="78f0b-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="78f0b-109">[v] Maximální počet `mdExportedType` tokenů, které mohou `rExportedTypes` být umístěny v poli.</span><span class="sxs-lookup"><span data-stu-id="78f0b-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="78f0b-110">[out] Počet tokenů `mdExportedType` skutečně umístěných v `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="78f0b-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f0b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78f0b-111">Return Value</span></span>  
  
|<span data-ttu-id="78f0b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78f0b-112">HRESULT</span></span>|<span data-ttu-id="78f0b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="78f0b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="78f0b-114">`EnumExportedTypes`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="78f0b-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="78f0b-115">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="78f0b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="78f0b-116">V tomto `pcTokens` případě je nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="78f0b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78f0b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78f0b-117">Requirements</span></span>  
 <span data-ttu-id="78f0b-118">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f0b-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f0b-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="78f0b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78f0b-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78f0b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78f0b-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f0b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f0b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="78f0b-122">See also</span></span>

- [<span data-ttu-id="78f0b-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78f0b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
