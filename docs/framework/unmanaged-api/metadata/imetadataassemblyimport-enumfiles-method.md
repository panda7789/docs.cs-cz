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
ms.openlocfilehash: b2ab06419491093a2de41d2ef25d16c01c03ebaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158844"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="29de8-102">IMetaDataAssemblyImport::EnumFiles – metoda</span><span class="sxs-lookup"><span data-stu-id="29de8-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="29de8-103">Vytvoří výčet souborů odkazovat v aktuálním manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="29de8-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29de8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29de8-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29de8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29de8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="29de8-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="29de8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="29de8-107">Musí to být hodnota null pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="29de8-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="29de8-108">[out] Pole používá k ukládání `mdFile` tokeny metadat.</span><span class="sxs-lookup"><span data-stu-id="29de8-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="29de8-109">[in] Maximální počet `mdFile` tokeny, které mohou být umístěny v `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="29de8-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="29de8-110">[out] Počet `mdFile` tokeny ve skutečnosti umístěny do `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="29de8-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29de8-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29de8-111">Return Value</span></span>  
  
|<span data-ttu-id="29de8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29de8-112">HRESULT</span></span>|<span data-ttu-id="29de8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="29de8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29de8-114">`EnumFiles` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="29de8-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29de8-115">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="29de8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="29de8-116">V takovém případě `pcTokens` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="29de8-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29de8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29de8-117">Requirements</span></span>  
 <span data-ttu-id="29de8-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29de8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29de8-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29de8-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29de8-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29de8-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29de8-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29de8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29de8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29de8-122">See also</span></span>

- [<span data-ttu-id="29de8-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29de8-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
