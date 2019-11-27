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
ms.openlocfilehash: 45e2348b4726447548544d975e60b93e464fb402
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450340"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="c73b7-102">IMetaDataAssemblyImport::EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="c73b7-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="c73b7-103">Vytvoří výčet exportovaných typů, na které odkazuje manifest sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="c73b7-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c73b7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c73b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c73b7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c73b7-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c73b7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c73b7-107">Při prvním volání metody `EnumExportedTypes` musí být hodnota null.</span><span class="sxs-lookup"><span data-stu-id="c73b7-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="c73b7-108">mimo Výčet `mdExportedType` tokeny metadat</span><span class="sxs-lookup"><span data-stu-id="c73b7-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c73b7-109">pro Maximální počet `mdExportedType` tokenů, které lze umístit do pole `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="c73b7-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c73b7-110">mimo Počet tokenů `mdExportedType` vlastněných v `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="c73b7-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c73b7-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c73b7-111">Return Value</span></span>  
  
|<span data-ttu-id="c73b7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c73b7-112">HRESULT</span></span>|<span data-ttu-id="c73b7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c73b7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c73b7-114">`EnumExportedTypes` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c73b7-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c73b7-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="c73b7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c73b7-116">V takovém případě je `pcTokens` nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="c73b7-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c73b7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c73b7-117">Requirements</span></span>  
 <span data-ttu-id="c73b7-118">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c73b7-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c73b7-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c73b7-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c73b7-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c73b7-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c73b7-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c73b7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73b7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c73b7-122">See also</span></span>

- [<span data-ttu-id="c73b7-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c73b7-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
