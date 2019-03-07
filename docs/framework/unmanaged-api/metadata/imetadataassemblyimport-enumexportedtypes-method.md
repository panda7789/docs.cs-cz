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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10982b34add7e42cb54872afdea96df82c1fdc54
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487908"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="42d5e-102">IMetaDataAssemblyImport::EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="42d5e-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="42d5e-103">Vytvoří výčet exportované typy odkazované v manifestu sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="42d5e-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42d5e-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42d5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42d5e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="42d5e-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="42d5e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="42d5e-107">Musí se jednat s hodnotou null hodnotu v případě `EnumExportedTypes` je metoda volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="42d5e-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="42d5e-108">[out] Výčet `mdExportedType` tokeny metadat.</span><span class="sxs-lookup"><span data-stu-id="42d5e-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="42d5e-109">[in] Maximální počet `mdExportedType` tokeny, které je možné umístit `rExportedTypes` pole.</span><span class="sxs-lookup"><span data-stu-id="42d5e-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="42d5e-110">[out] Počet `mdExportedType` tokeny ve skutečnosti umístěny do `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="42d5e-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42d5e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42d5e-111">Return Value</span></span>  
  
|<span data-ttu-id="42d5e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42d5e-112">HRESULT</span></span>|<span data-ttu-id="42d5e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="42d5e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="42d5e-114">`EnumExportedTypes` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="42d5e-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="42d5e-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="42d5e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="42d5e-116">V takovém případě `pcTokens` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="42d5e-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42d5e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42d5e-117">Requirements</span></span>  
 <span data-ttu-id="42d5e-118">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42d5e-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42d5e-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42d5e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42d5e-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42d5e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="42d5e-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42d5e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d5e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42d5e-122">See also</span></span>
- [<span data-ttu-id="42d5e-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42d5e-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
