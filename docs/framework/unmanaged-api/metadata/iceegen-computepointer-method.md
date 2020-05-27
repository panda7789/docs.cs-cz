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
ms.openlocfilehash: 206dcd3a0a82da9b6211c8c2045e4e9d3d991973
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008869"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="c47e6-102">ICeeGen::ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="c47e6-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="c47e6-103">Určuje vyrovnávací paměť pro zadaný oddíl kódu.</span><span class="sxs-lookup"><span data-stu-id="c47e6-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="c47e6-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="c47e6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c47e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c47e6-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c47e6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c47e6-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="c47e6-107">pro Oddíl kódu, pro který se má vrátit vyrovnávací paměť</span><span class="sxs-lookup"><span data-stu-id="c47e6-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="c47e6-108">pro Relativní virtuální adresa metody, pro kterou se má získat ukazatel</span><span class="sxs-lookup"><span data-stu-id="c47e6-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="c47e6-109">mimo Ukazatel na vrácenou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="c47e6-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c47e6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c47e6-110">Requirements</span></span>  
 <span data-ttu-id="c47e6-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c47e6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c47e6-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c47e6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c47e6-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c47e6-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c47e6-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c47e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c47e6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c47e6-115">See also</span></span>

- [<span data-ttu-id="c47e6-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c47e6-116">ICeeGen Interface</span></span>](iceegen-interface.md)
