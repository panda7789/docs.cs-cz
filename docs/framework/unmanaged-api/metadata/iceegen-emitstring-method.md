---
title: ICeeGen::EmitString – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dccb2a3a3f3aaf0f209c8f3543056ab81c562dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443896"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="dd7c6-102">ICeeGen::EmitString – metoda</span><span class="sxs-lookup"><span data-stu-id="dd7c6-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="dd7c6-103">Zadaný řetězec vysílá do základu kódu.</span><span class="sxs-lookup"><span data-stu-id="dd7c6-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="dd7c6-104">Tato metoda je zastaralá a by se neměla používat.</span><span class="sxs-lookup"><span data-stu-id="dd7c6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd7c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd7c6-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd7c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd7c6-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="dd7c6-107">[v] Řetězec pro vydávání.</span><span class="sxs-lookup"><span data-stu-id="dd7c6-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="dd7c6-108">[out] Relativní virtuální adresa emitovaného řetězec.</span><span class="sxs-lookup"><span data-stu-id="dd7c6-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd7c6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd7c6-109">Requirements</span></span>  
 <span data-ttu-id="dd7c6-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd7c6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd7c6-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd7c6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd7c6-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd7c6-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd7c6-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd7c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7c6-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd7c6-114">See Also</span></span>  
 [<span data-ttu-id="dd7c6-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd7c6-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
