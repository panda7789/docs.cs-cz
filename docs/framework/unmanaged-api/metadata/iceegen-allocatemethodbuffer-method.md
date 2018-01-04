---
title: "ICeeGen::AllocateMethodBuffer – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AllocateMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b92d42878e9f3a8778208d8acf89de7618fc7c54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="00485-102">ICeeGen::AllocateMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="00485-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="00485-103">Vytvoří vyrovnávací paměti zadaná velikost pro metodu a získá relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="00485-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="00485-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="00485-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00485-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00485-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00485-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="00485-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="00485-107">[v] Délka vyrovnávací paměti k vytvoření.</span><span class="sxs-lookup"><span data-stu-id="00485-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="00485-108">[out] Vrácený vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="00485-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="00485-109">[out] Relativní virtuální adresa metodu.</span><span class="sxs-lookup"><span data-stu-id="00485-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00485-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00485-110">Requirements</span></span>  
 <span data-ttu-id="00485-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00485-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00485-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00485-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00485-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00485-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00485-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00485-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00485-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="00485-115">See Also</span></span>  
 [<span data-ttu-id="00485-116">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00485-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
