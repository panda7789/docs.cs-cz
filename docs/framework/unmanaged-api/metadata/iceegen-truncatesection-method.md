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
ms.openlocfilehash: 1036d6080bf17eea288724c7980ce53dfa2121f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116318"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="366c7-102">ICeeGen::TruncateSection – metoda</span><span class="sxs-lookup"><span data-stu-id="366c7-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="366c7-103">Zkrátí části zadaný kód pomocí zadané délky.</span><span class="sxs-lookup"><span data-stu-id="366c7-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="366c7-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="366c7-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="366c7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="366c7-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="366c7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="366c7-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="366c7-107">[in] V části došlo ke zkrácení.</span><span class="sxs-lookup"><span data-stu-id="366c7-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="366c7-108">[in] Délka v bajtech, podle kterého chcete zkrátit části.</span><span class="sxs-lookup"><span data-stu-id="366c7-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="366c7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="366c7-109">Remarks</span></span>  
 <span data-ttu-id="366c7-110">Volání `TruncateSection` pouze v případě, že máte zvláštní oddíl s požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="366c7-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="366c7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="366c7-111">Requirements</span></span>  
 <span data-ttu-id="366c7-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="366c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="366c7-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="366c7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="366c7-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="366c7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="366c7-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="366c7-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="366c7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="366c7-116">See also</span></span>

- [<span data-ttu-id="366c7-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="366c7-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
