---
title: "ICeeGen::GetSectionCreate – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a069f65d3059bfa427ea20623ff9a2ac4049fd39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="f5363-102">ICeeGen::GetSectionCreate – metoda</span><span class="sxs-lookup"><span data-stu-id="f5363-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="f5363-103">Generuje a získá oddíl kód pomocí zadaného názvu a hodnoty příznaku.</span><span class="sxs-lookup"><span data-stu-id="f5363-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="f5363-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="f5363-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5363-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5363-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5363-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5363-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f5363-107">[v] Ukazatel na řetězec, který určuje název oddílu, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="f5363-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="f5363-108">[v] Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="f5363-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="f5363-109">[out] Ukazatel na nově vytvořený kód části.</span><span class="sxs-lookup"><span data-stu-id="f5363-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5363-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5363-110">Remarks</span></span>  
 <span data-ttu-id="f5363-111">Volání `GetSectionCreate` pouze v případě, že máte speciální části požadavky, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="f5363-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5363-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5363-112">Requirements</span></span>  
 <span data-ttu-id="f5363-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5363-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5363-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f5363-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5363-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5363-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5363-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5363-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5363-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5363-117">See Also</span></span>  
 [<span data-ttu-id="f5363-118">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5363-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
