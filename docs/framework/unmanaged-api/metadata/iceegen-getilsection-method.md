---
title: ICeeGen::GetIlSection – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cff5b7fadf4345b7a1d09911dc7061adc925e7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992612"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="9c12d-102">ICeeGen::GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="9c12d-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="9c12d-103">Získá části základu kódu IL odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="9c12d-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="9c12d-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="9c12d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c12d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c12d-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c12d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c12d-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="9c12d-107">[in] Popisovač oddílu, který má získat.</span><span class="sxs-lookup"><span data-stu-id="9c12d-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c12d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c12d-108">Requirements</span></span>  
 <span data-ttu-id="9c12d-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c12d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c12d-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c12d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c12d-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c12d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c12d-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c12d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c12d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c12d-113">See also</span></span>

- [<span data-ttu-id="9c12d-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c12d-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
