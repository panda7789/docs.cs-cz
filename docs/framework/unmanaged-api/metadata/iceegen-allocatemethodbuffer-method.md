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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd51f9c05c49fefc790ce69dcdc3117680c8e6b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500027"
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="a53b2-102">ICeeGen::AllocateMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="a53b2-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="a53b2-103">Vytvoří vyrovnávací paměti o zadané velikosti pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="a53b2-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="a53b2-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="a53b2-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a53b2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a53b2-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a53b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a53b2-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="a53b2-107">[in] Délka vyrovnávací paměti k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="a53b2-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a53b2-108">[out] Vrácené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a53b2-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="a53b2-109">[out] Relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="a53b2-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a53b2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a53b2-110">Requirements</span></span>  
 <span data-ttu-id="a53b2-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a53b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a53b2-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a53b2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a53b2-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a53b2-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a53b2-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a53b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53b2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a53b2-115">See also</span></span>
- [<span data-ttu-id="a53b2-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a53b2-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
