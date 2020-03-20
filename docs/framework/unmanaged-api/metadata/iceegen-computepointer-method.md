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
ms.openlocfilehash: 9587bbe8f087fd9a51bba67492af1d5acb53ae4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176094"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="86196-102">ICeeGen::ComputePointer – metoda</span><span class="sxs-lookup"><span data-stu-id="86196-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="86196-103">Určuje vyrovnávací paměť pro zadaný kód části.</span><span class="sxs-lookup"><span data-stu-id="86196-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="86196-104">Tato metoda je zastaralá a neměla by být použita.</span><span class="sxs-lookup"><span data-stu-id="86196-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86196-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86196-105">Syntax</span></span>  
  
```cpp  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,
    [out] UCHAR        **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86196-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="86196-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="86196-107">[v] Část kódu, pro kterou chcete vrátit vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="86196-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="86196-108">[v] Relativní virtuální adresa metody, pro kterou chcete získat ukazatel.</span><span class="sxs-lookup"><span data-stu-id="86196-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="86196-109">[out] Ukazatel na vrácenou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="86196-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86196-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86196-110">Requirements</span></span>  
 <span data-ttu-id="86196-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86196-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86196-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="86196-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86196-113">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86196-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86196-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86196-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86196-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="86196-115">See also</span></span>

- [<span data-ttu-id="86196-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86196-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
