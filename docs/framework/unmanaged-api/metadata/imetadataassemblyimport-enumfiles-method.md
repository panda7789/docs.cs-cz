---
title: IMetaDataAssemblyImport::EnumFiles – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: ed8bafd67b5d55a5116111b7721fbdc31c52aca6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009091"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="f7e06-102">IMetaDataAssemblyImport::EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="f7e06-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="f7e06-103">Vytvoří výčet souborů odkazovaných v aktuálním manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f7e06-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e06-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7e06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7e06-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f7e06-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f7e06-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f7e06-107">Pro první volání této metody musí být hodnota null.</span><span class="sxs-lookup"><span data-stu-id="f7e06-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="f7e06-108">mimo Pole použité pro ukládání `mdFile` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="f7e06-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f7e06-109">pro Maximální počet `mdFile` tokenů, které lze umístit do `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="f7e06-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f7e06-110">mimo Počet tokenů, které jsou `mdFile` ve skutečnosti umístěny v `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="f7e06-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7e06-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7e06-111">Return Value</span></span>  
  
|<span data-ttu-id="f7e06-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7e06-112">HRESULT</span></span>|<span data-ttu-id="f7e06-113">Description</span><span class="sxs-lookup"><span data-stu-id="f7e06-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f7e06-114">`EnumFiles`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f7e06-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f7e06-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="f7e06-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f7e06-116">V tomto případě `pcTokens` je nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="f7e06-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7e06-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7e06-117">Requirements</span></span>  
 <span data-ttu-id="f7e06-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e06-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e06-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f7e06-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7e06-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f7e06-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7e06-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e06-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e06-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7e06-122">See also</span></span>

- [<span data-ttu-id="f7e06-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7e06-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
