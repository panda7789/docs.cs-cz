---
title: ICeeGen::AllocateMethodBuffer – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
ms.openlocfilehash: 38b9ea2ffab439f55f0a6d34d7f42c7669629168
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177914"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="78012-102">ICeeGen::AllocateMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="78012-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="78012-103">Vytvoří vyrovnávací paměť zadané velikosti pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="78012-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="78012-104">Tato metoda je zastaralá a neměla by být použita.</span><span class="sxs-lookup"><span data-stu-id="78012-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78012-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78012-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocateMethodBuffer (
    [in]  ULONG    cchBuffer,
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78012-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="78012-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="78012-107">[v] Délka vyrovnávací paměti vytvořit.</span><span class="sxs-lookup"><span data-stu-id="78012-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="78012-108">[out] Vrácená vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="78012-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="78012-109">[out] Relativní virtuální adresa metody.</span><span class="sxs-lookup"><span data-stu-id="78012-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78012-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78012-110">Requirements</span></span>  
 <span data-ttu-id="78012-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78012-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78012-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="78012-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78012-113">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78012-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78012-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78012-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78012-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="78012-115">See also</span></span>

- [<span data-ttu-id="78012-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78012-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
