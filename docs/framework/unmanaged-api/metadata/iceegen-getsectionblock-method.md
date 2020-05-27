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
ms.openlocfilehash: ed534890fc90d3b8543a1166c85903f10163f0a8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008316"
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="5b586-102">ICeeGen::GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="5b586-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="5b586-103">Získá blok oddílu základu kódu.</span><span class="sxs-lookup"><span data-stu-id="5b586-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="5b586-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="5b586-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b586-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b586-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="5b586-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b586-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="5b586-107">pro Oddíl, ze kterého má být načten blok základního kódu.</span><span class="sxs-lookup"><span data-stu-id="5b586-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="5b586-108">pro Délka bloku, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="5b586-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="5b586-109">pro Bajt relativní ke začátku oddílu, s nímž má být zarovnaný první bajt bloku.</span><span class="sxs-lookup"><span data-stu-id="5b586-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="5b586-110">Toto je pozice bloku v rámci oddílu.</span><span class="sxs-lookup"><span data-stu-id="5b586-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="5b586-111">mimo Ukazatel na umístění, které přijímá adresu načteného bloku.</span><span class="sxs-lookup"><span data-stu-id="5b586-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b586-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b586-112">Remarks</span></span>  
 <span data-ttu-id="5b586-113">Volejte `GetSectionBlock` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="5b586-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b586-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b586-114">Requirements</span></span>  
 <span data-ttu-id="5b586-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b586-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b586-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5b586-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b586-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="5b586-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5b586-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b586-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b586-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b586-119">See also</span></span>

- [<span data-ttu-id="5b586-120">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b586-120">ICeeGen Interface</span></span>](iceegen-interface.md)
