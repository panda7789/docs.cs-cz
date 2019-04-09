---
title: ICeeGen::GetStringSection – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef22114b582ebfc9714dedc0cb6e66594d945ca1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083787"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="d4b62-102">ICeeGen::GetStringSection – metoda</span><span class="sxs-lookup"><span data-stu-id="d4b62-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="d4b62-103">Získá řetězcovou reprezentaci části kódu, který odkazuje Zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="d4b62-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="d4b62-104">Tato metoda je zastaralý a neměl by se používat.</span><span class="sxs-lookup"><span data-stu-id="d4b62-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b62-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b62-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4b62-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4b62-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d4b62-107">[out v] Popisovač na části kódu.</span><span class="sxs-lookup"><span data-stu-id="d4b62-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4b62-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4b62-108">Requirements</span></span>  
 <span data-ttu-id="d4b62-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4b62-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4b62-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d4b62-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4b62-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4b62-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d4b62-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d4b62-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4b62-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4b62-113">See also</span></span>

- [<span data-ttu-id="d4b62-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4b62-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
