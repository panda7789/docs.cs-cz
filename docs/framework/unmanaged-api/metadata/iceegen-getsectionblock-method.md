---
title: ICeeGen::GetSectionBlock – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
ms.openlocfilehash: a494b1aaa762549528e92ab93d18929ef73eb8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176081"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="8147d-102">ICeeGen::GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="8147d-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="8147d-103">Získá blok oddílu základu kódu.</span><span class="sxs-lookup"><span data-stu-id="8147d-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="8147d-104">Tato metoda je zastaralá a neměla by být použita.</span><span class="sxs-lookup"><span data-stu-id="8147d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8147d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8147d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="8147d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8147d-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8147d-107">[v] Oddíl, ze kterého chcete načíst blok základu kódu.</span><span class="sxs-lookup"><span data-stu-id="8147d-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="8147d-108">[v] Délka bloku, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="8147d-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="8147d-109">[v] Bajt, vzhledem k začátku oddílu, se kterým chcete zarovnat první bajt bloku.</span><span class="sxs-lookup"><span data-stu-id="8147d-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="8147d-110">Toto je pozice bloku v sekci.</span><span class="sxs-lookup"><span data-stu-id="8147d-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="8147d-111">[out] Ukazatel na umístění, které přijímá adresu načteného bloku.</span><span class="sxs-lookup"><span data-stu-id="8147d-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8147d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8147d-112">Remarks</span></span>  
 <span data-ttu-id="8147d-113">Volání `GetSectionBlock` pouze v případě, že máte zvláštní požadavky oddílu, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="8147d-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8147d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8147d-114">Requirements</span></span>  
 <span data-ttu-id="8147d-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8147d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8147d-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="8147d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8147d-117">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8147d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8147d-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8147d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8147d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8147d-119">See also</span></span>

- [<span data-ttu-id="8147d-120">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8147d-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
