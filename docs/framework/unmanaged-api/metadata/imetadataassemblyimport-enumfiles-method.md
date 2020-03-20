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
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177819"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="2ddec-102">IMetaDataAssemblyImport::EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="2ddec-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="2ddec-103">Vyjmenovává soubory odkazované v aktuálním manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ddec-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ddec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ddec-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ddec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ddec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2ddec-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="2ddec-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2ddec-107">To musí být hodnota null pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="2ddec-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="2ddec-108">[out] Pole používané k `mdFile` ukládání tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="2ddec-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2ddec-109">[v] Maximální počet `mdFile` tokenů, které mohou `rFiles`být umístěny v .</span><span class="sxs-lookup"><span data-stu-id="2ddec-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2ddec-110">[out] Počet tokenů `mdFile` skutečně umístěných v `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="2ddec-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ddec-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ddec-111">Return Value</span></span>  
  
|<span data-ttu-id="2ddec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ddec-112">HRESULT</span></span>|<span data-ttu-id="2ddec-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2ddec-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2ddec-114">`EnumFiles`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2ddec-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2ddec-115">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="2ddec-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2ddec-116">V tomto `pcTokens` případě je nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="2ddec-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ddec-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ddec-117">Requirements</span></span>  
 <span data-ttu-id="2ddec-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ddec-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ddec-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="2ddec-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ddec-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ddec-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ddec-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ddec-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ddec-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ddec-122">See also</span></span>

- [<span data-ttu-id="2ddec-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ddec-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
