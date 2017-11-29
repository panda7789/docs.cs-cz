---
title: "ICeeGen::ComputePointer – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.ComputePointer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c1f5f1c0ea5672812fca387b34238ada2a109938
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="efccf-102">ICeeGen::ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="efccf-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="efccf-103">Určuje velikost vyrovnávací paměti pro část zadaný kód.</span><span class="sxs-lookup"><span data-stu-id="efccf-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="efccf-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="efccf-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efccf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efccf-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efccf-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="efccf-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="efccf-107">[v] Části kódu, pro které chcete vrátit do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="efccf-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="efccf-108">[v] Relativní virtuální adresa metody, pro které chcete získat ukazatel.</span><span class="sxs-lookup"><span data-stu-id="efccf-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="efccf-109">[out] Ukazatel na vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="efccf-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efccf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efccf-110">Requirements</span></span>  
 <span data-ttu-id="efccf-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efccf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efccf-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="efccf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efccf-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="efccf-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efccf-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efccf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efccf-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="efccf-115">See Also</span></span>  
 [<span data-ttu-id="efccf-116">Iceegen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efccf-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
