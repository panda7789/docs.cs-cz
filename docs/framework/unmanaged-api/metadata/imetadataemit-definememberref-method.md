---
title: IMetaDataEmit::DefineMemberRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad2b3e5c452a5fc79e7a1cc0342cfc1d119a5fbd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481986"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="30adc-102">IMetaDataEmit::DefineMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="30adc-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="30adc-103">Definuje odkaz na člena modulu mimo aktuální obor a získá token pro tuto definici odkazu.</span><span class="sxs-lookup"><span data-stu-id="30adc-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30adc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30adc-104">Syntax</span></span>  
  
```  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30adc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30adc-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="30adc-106">[in] Token pro cílový člen třídy nebo rozhraní, pokud člen není globální; Pokud je globální, člen `mdModuleRef` token pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="30adc-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="30adc-107">[in] Jméno člena cíl.</span><span class="sxs-lookup"><span data-stu-id="30adc-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="30adc-108">[in] Podpis cílové člena.</span><span class="sxs-lookup"><span data-stu-id="30adc-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="30adc-109">[in] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="30adc-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="30adc-110">[out] `mdMemberRef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="30adc-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30adc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30adc-111">Requirements</span></span>  
 <span data-ttu-id="30adc-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30adc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30adc-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="30adc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30adc-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30adc-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30adc-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30adc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30adc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30adc-116">See also</span></span>
- [<span data-ttu-id="30adc-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30adc-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="30adc-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30adc-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
