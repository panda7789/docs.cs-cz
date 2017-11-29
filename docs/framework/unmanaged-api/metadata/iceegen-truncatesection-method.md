---
title: "ICeeGen::TruncateSection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.TruncateSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 204c71b55c4ba2ec1e3b137137d8f08845b12e49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="0cde6-102">ICeeGen::TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="0cde6-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="0cde6-103">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="0cde6-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="0cde6-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="0cde6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cde6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cde6-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0cde6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cde6-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="0cde6-107">[v] V části zkrátit.</span><span class="sxs-lookup"><span data-stu-id="0cde6-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="0cde6-108">[v] Délka v bajtech, podle kterého zkrátit části.</span><span class="sxs-lookup"><span data-stu-id="0cde6-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cde6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cde6-109">Remarks</span></span>  
 <span data-ttu-id="0cde6-110">Volání `TruncateSection` pouze v případě, že máte speciální části požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="0cde6-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cde6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cde6-111">Requirements</span></span>  
 <span data-ttu-id="0cde6-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cde6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cde6-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0cde6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0cde6-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0cde6-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0cde6-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cde6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cde6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cde6-116">See Also</span></span>  
 [<span data-ttu-id="0cde6-117">Iceegen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cde6-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
