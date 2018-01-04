---
title: "ICeeGen::GetSectionDataLen – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionDataLen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 217a6c87d5152b68e062d9c2a64ec78478f301cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="3ec79-102">ICeeGen::GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="3ec79-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="3ec79-103">Získá délku zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="3ec79-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="3ec79-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="3ec79-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec79-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ec79-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ec79-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ec79-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="3ec79-107">[v] Část dat, jehož délka bude načten.</span><span class="sxs-lookup"><span data-stu-id="3ec79-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="3ec79-108">[out] Vrácená délka zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="3ec79-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ec79-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ec79-109">Remarks</span></span>  
 <span data-ttu-id="3ec79-110">Volání `GetSectionDataLen` pouze v případě, že máte speciální části požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="3ec79-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ec79-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ec79-111">Requirements</span></span>  
 <span data-ttu-id="3ec79-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ec79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ec79-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ec79-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ec79-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ec79-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ec79-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ec79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ec79-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ec79-116">See Also</span></span>  
 [<span data-ttu-id="3ec79-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec79-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
