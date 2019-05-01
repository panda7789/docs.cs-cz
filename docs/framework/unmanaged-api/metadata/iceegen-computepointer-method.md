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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992625"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="4cdca-102">ICeeGen::ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="4cdca-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="4cdca-103">Určuje vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="4cdca-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="4cdca-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="4cdca-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cdca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cdca-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cdca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4cdca-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="4cdca-107">[in] Části kódu, pro které chcete vrátit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4cdca-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="4cdca-108">[in] Relativní virtuální adresu metody, pro které chcete získat ukazatel.</span><span class="sxs-lookup"><span data-stu-id="4cdca-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="4cdca-109">[out] Ukazatel na vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4cdca-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cdca-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4cdca-110">Requirements</span></span>  
 <span data-ttu-id="4cdca-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cdca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cdca-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4cdca-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4cdca-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4cdca-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4cdca-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cdca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cdca-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cdca-115">See also</span></span>

- [<span data-ttu-id="4cdca-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4cdca-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
