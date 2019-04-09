---
title: ICeeGen::ComputePointer – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79ef272e0c8afa0cd1942416c3a5eb9b825c2e6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145142"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="acbfa-102">ICeeGen::ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="acbfa-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="acbfa-103">Určuje vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="acbfa-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="acbfa-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="acbfa-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbfa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acbfa-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acbfa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="acbfa-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="acbfa-107">[in] Části kódu, pro které chcete vrátit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="acbfa-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="acbfa-108">[in] Relativní virtuální adresu metody, pro které chcete získat ukazatel.</span><span class="sxs-lookup"><span data-stu-id="acbfa-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="acbfa-109">[out] Ukazatel na vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="acbfa-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acbfa-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="acbfa-110">Requirements</span></span>  
 <span data-ttu-id="acbfa-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acbfa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acbfa-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="acbfa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="acbfa-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="acbfa-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="acbfa-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="acbfa-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="acbfa-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acbfa-115">See also</span></span>

- [<span data-ttu-id="acbfa-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="acbfa-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
