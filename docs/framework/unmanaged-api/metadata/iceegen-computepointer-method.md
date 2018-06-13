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
ms.openlocfilehash: a1239546072192d6ff9497013ad7b7140ea13085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443239"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="7a795-102">ICeeGen::ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="7a795-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="7a795-103">Určuje velikost vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="7a795-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="7a795-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="7a795-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a795-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a795-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a795-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a795-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7a795-107">[v] Části kódu, pro které chcete vrátit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7a795-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="7a795-108">[v] Relativní virtuální adresa metody, pro které chcete získat ukazatel.</span><span class="sxs-lookup"><span data-stu-id="7a795-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="7a795-109">[out] Ukazatel na vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7a795-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a795-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a795-110">Requirements</span></span>  
 <span data-ttu-id="7a795-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a795-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a795-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7a795-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a795-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a795-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a795-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a795-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a795-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a795-115">See Also</span></span>  
 [<span data-ttu-id="7a795-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a795-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
