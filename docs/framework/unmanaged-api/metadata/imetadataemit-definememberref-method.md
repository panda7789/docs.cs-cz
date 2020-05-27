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
ms.openlocfilehash: 576f4561ed782f091840ac378831110a1bfef9c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004687"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="8f585-102">IMetaDataEmit::DefineMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="8f585-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="8f585-103">Definuje odkaz na člena modulu mimo aktuální rozsah a získá token do této referenční definice.</span><span class="sxs-lookup"><span data-stu-id="8f585-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f585-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f585-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f585-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f585-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="8f585-106">pro Token pro třídu nebo rozhraní cílového člena, pokud člen není globální; Pokud je člen globální, `mdModuleRef` token pro tento jiný soubor.</span><span class="sxs-lookup"><span data-stu-id="8f585-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="8f585-107">pro Název cílového člena.</span><span class="sxs-lookup"><span data-stu-id="8f585-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8f585-108">pro Signatura cílového člena.</span><span class="sxs-lookup"><span data-stu-id="8f585-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8f585-109">pro Počet bajtů v `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="8f585-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="8f585-110">mimo `mdMemberRef`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="8f585-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f585-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f585-111">Requirements</span></span>  
 <span data-ttu-id="8f585-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f585-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f585-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8f585-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f585-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="8f585-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f585-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f585-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f585-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f585-116">See also</span></span>

- [<span data-ttu-id="8f585-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f585-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8f585-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f585-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
