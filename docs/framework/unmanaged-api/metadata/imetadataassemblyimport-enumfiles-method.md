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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32c402b20f9d7f0d370cfa6ec8376603efa8c3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777989"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="d6dbe-102">IMetaDataAssemblyImport::EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="d6dbe-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="d6dbe-103">Vytvoří výčet souborů odkazovat v aktuálním manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6dbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6dbe-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6dbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6dbe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d6dbe-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d6dbe-107">Musí to být hodnota null pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="d6dbe-108">[out] Pole používá k ukládání `mdFile` tokeny metadat.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d6dbe-109">[in] Maximální počet `mdFile` tokeny, které mohou být umístěny v `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d6dbe-110">[out] Počet `mdFile` tokeny ve skutečnosti umístěny do `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6dbe-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6dbe-111">Return Value</span></span>  
  
|<span data-ttu-id="d6dbe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6dbe-112">HRESULT</span></span>|<span data-ttu-id="d6dbe-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d6dbe-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6dbe-114">`EnumFiles` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d6dbe-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d6dbe-116">V takovém případě `pcTokens` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="d6dbe-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6dbe-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6dbe-117">Requirements</span></span>  
 <span data-ttu-id="d6dbe-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6dbe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6dbe-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6dbe-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6dbe-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6dbe-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6dbe-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6dbe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6dbe-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6dbe-122">See also</span></span>

- [<span data-ttu-id="d6dbe-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6dbe-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
