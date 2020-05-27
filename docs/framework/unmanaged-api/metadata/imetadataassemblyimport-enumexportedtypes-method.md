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
ms.openlocfilehash: 514488c6e0d2e89de0d8ee483def485ec9f3ef25
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009098"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="e54a1-102">IMetaDataAssemblyImport::EnumExportedTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="e54a1-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="e54a1-103">Vytvoří výčet exportovaných typů, na které odkazuje manifest sestavení v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="e54a1-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e54a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e54a1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e54a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e54a1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e54a1-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e54a1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e54a1-107">Při prvním volání metody musí být hodnota null `EnumExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="e54a1-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="e54a1-108">mimo Výčet `mdExportedType` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="e54a1-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e54a1-109">pro Maximální počet `mdExportedType` tokenů, které mohou být umístěny v `rExportedTypes` poli.</span><span class="sxs-lookup"><span data-stu-id="e54a1-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e54a1-110">mimo Počet tokenů, které jsou `mdExportedType` ve skutečnosti umístěny v `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="e54a1-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e54a1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e54a1-111">Return Value</span></span>  
  
|<span data-ttu-id="e54a1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e54a1-112">HRESULT</span></span>|<span data-ttu-id="e54a1-113">Description</span><span class="sxs-lookup"><span data-stu-id="e54a1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e54a1-114">`EnumExportedTypes`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e54a1-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e54a1-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="e54a1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e54a1-116">V tomto případě `pcTokens` je nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="e54a1-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e54a1-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e54a1-117">Requirements</span></span>  
 <span data-ttu-id="e54a1-118">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e54a1-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e54a1-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e54a1-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e54a1-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="e54a1-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e54a1-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e54a1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54a1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e54a1-122">See also</span></span>

- [<span data-ttu-id="e54a1-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e54a1-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
