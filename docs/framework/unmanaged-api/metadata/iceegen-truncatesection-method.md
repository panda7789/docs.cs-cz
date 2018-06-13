---
title: ICeeGen::TruncateSection – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7b21179faec0b6f37b8084c9ee8a0bfd327193e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443561"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="c55f5-102">ICeeGen::TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="c55f5-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="c55f5-103">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="c55f5-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="c55f5-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="c55f5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55f5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c55f5-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c55f5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c55f5-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="c55f5-107">[v] V části zkrátit.</span><span class="sxs-lookup"><span data-stu-id="c55f5-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="c55f5-108">[v] Délka v bajtech, podle kterého zkrátit části.</span><span class="sxs-lookup"><span data-stu-id="c55f5-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c55f5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c55f5-109">Remarks</span></span>  
 <span data-ttu-id="c55f5-110">Volání `TruncateSection` pouze v případě, že máte speciální části požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="c55f5-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55f5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c55f5-111">Requirements</span></span>  
 <span data-ttu-id="c55f5-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c55f5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c55f5-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c55f5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c55f5-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c55f5-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c55f5-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c55f5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55f5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c55f5-116">See Also</span></span>  
 [<span data-ttu-id="c55f5-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c55f5-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
