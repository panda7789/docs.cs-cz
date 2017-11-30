---
title: "ICeeGen::GetSectionBlock – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="ec4b1-102">ICeeGen::GetSectionBlock – metoda</span><span class="sxs-lookup"><span data-stu-id="ec4b1-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="ec4b1-103">Získá blok část základu kódu.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="ec4b1-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec4b1-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec4b1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec4b1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ec4b1-107">[v] V části, ze kterého chcete načíst blok základu kódu.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="ec4b1-108">[v] Délka bloku mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="ec4b1-109">[v] Byte relativně k začátku části, se kterým chcete-li zarovnat prvním bajtem bloku.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="ec4b1-110">Toto je umístění bloku v rámci oddílu.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="ec4b1-111">[out] Ukazatel na umístění, která přijímá adresu načtené bloku.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4b1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec4b1-112">Remarks</span></span>  
 <span data-ttu-id="ec4b1-113">Volání `GetSectionBlock` pouze v případě, že máte speciální části požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="ec4b1-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4b1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec4b1-114">Requirements</span></span>  
 <span data-ttu-id="ec4b1-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec4b1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4b1-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ec4b1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec4b1-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec4b1-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec4b1-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4b1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec4b1-119">See Also</span></span>  
 [<span data-ttu-id="ec4b1-120">Iceegen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec4b1-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
