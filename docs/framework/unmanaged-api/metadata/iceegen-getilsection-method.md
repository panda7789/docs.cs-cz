---
title: "ICeeGen::GetIlSection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetIlSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4805e9421a80954c01ba1ffb6e04332c07e5d84e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="70cda-102">ICeeGen::GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="70cda-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="70cda-103">Získá části základní převodní jazyk kódu Zadaný popisovač odkazuje.</span><span class="sxs-lookup"><span data-stu-id="70cda-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="70cda-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="70cda-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cda-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70cda-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70cda-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="70cda-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="70cda-107">[v] Popisovač do části získat.</span><span class="sxs-lookup"><span data-stu-id="70cda-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70cda-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70cda-108">Requirements</span></span>  
 <span data-ttu-id="70cda-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70cda-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70cda-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="70cda-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70cda-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70cda-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70cda-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70cda-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70cda-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="70cda-113">See Also</span></span>  
 [<span data-ttu-id="70cda-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70cda-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
