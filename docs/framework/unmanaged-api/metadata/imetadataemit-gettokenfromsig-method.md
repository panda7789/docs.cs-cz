---
title: IMetaDataEmit::GetTokenFromSig – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afc2192fe46ed75ed6fb75e0d58268152856b746
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770776"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="9fe42-102">IMetaDataEmit::GetTokenFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="9fe42-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="9fe42-103">Získá token pro Zadaná metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="9fe42-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fe42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fe42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fe42-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="9fe42-106">[in] Podpis trvale uložila a uložené.</span><span class="sxs-lookup"><span data-stu-id="9fe42-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="9fe42-107">[in] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="9fe42-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="9fe42-108">[out] `mdSignature` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="9fe42-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe42-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fe42-109">Requirements</span></span>  
 <span data-ttu-id="9fe42-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fe42-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe42-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9fe42-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9fe42-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fe42-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fe42-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe42-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe42-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fe42-114">See also</span></span>

- [<span data-ttu-id="9fe42-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fe42-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9fe42-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fe42-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
