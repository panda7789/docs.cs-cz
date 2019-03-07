---
title: ICeeGen::EmitString – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ddd3b5cc79cedba6d6acc6a9b6b70c00d917fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476227"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="20914-102">ICeeGen::EmitString – metoda</span><span class="sxs-lookup"><span data-stu-id="20914-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="20914-103">Zadaný řetězec vysílá do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="20914-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="20914-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="20914-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20914-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20914-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20914-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="20914-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="20914-107">[in] Řetězec, který se má vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="20914-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="20914-108">[out] Relativní virtuální adresu emitovaný řetězce.</span><span class="sxs-lookup"><span data-stu-id="20914-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20914-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20914-109">Requirements</span></span>  
 <span data-ttu-id="20914-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20914-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20914-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20914-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20914-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20914-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="20914-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20914-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20914-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20914-114">See also</span></span>
- [<span data-ttu-id="20914-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20914-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
