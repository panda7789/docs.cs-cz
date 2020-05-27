---
title: IMetaDataAssemblyImport::EnumAssemblyRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 1b9700455da82fc7f4a39d4c208ac0b18ef79722
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009116"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="b216a-102">IMetaDataAssemblyImport::EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="b216a-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="b216a-103">Vytvoří výčet `mdAssemblyRef` instancí, které jsou definovány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b216a-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b216a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b216a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b216a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b216a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b216a-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b216a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b216a-107">Při prvním volání metody musí být hodnota null `EnumAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="b216a-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="b216a-108">mimo Výčet `mdAssemblyRef` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="b216a-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b216a-109">pro Maximální počet tokenů, které mohou být umístěny v `rAssemblyRefs` poli.</span><span class="sxs-lookup"><span data-stu-id="b216a-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b216a-110">mimo Počet tokenů, které jsou ve skutečnosti umístěny v `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="b216a-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b216a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b216a-111">Return Value</span></span>  
  
|<span data-ttu-id="b216a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b216a-112">HRESULT</span></span>|<span data-ttu-id="b216a-113">Description</span><span class="sxs-lookup"><span data-stu-id="b216a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b216a-114">`EnumAssemblyRefs`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b216a-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b216a-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="b216a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b216a-116">V tomto případě `pcTokens` je nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="b216a-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b216a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b216a-117">Requirements</span></span>  
 <span data-ttu-id="b216a-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b216a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b216a-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b216a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b216a-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b216a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b216a-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b216a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b216a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b216a-122">See also</span></span>

- [<span data-ttu-id="b216a-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b216a-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
