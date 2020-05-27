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
ms.openlocfilehash: dbbfa77ee76770bcf1d662bc5ae179909eaf3b25
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008284"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="57650-102">ICeeGen::GetStringSection – metoda</span><span class="sxs-lookup"><span data-stu-id="57650-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="57650-103">Načte řetězcovou reprezentaci oddílu kódu, na který odkazuje zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="57650-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="57650-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="57650-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57650-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57650-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57650-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="57650-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="57650-107">[in, out] Popisovač části kódu.</span><span class="sxs-lookup"><span data-stu-id="57650-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57650-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57650-108">Requirements</span></span>  
 <span data-ttu-id="57650-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57650-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57650-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="57650-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57650-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="57650-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57650-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57650-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57650-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="57650-113">See also</span></span>

- [<span data-ttu-id="57650-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57650-114">ICeeGen Interface</span></span>](iceegen-interface.md)
