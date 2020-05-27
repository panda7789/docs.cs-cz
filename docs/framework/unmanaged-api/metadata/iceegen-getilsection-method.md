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
ms.openlocfilehash: 05f39befa8966046cd71db82da37c44f20992cff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008804"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="2d59a-102">ICeeGen::GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="2d59a-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="2d59a-103">Získá část základu kódu zprostředkujícího jazyka, na kterou odkazuje zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="2d59a-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="2d59a-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="2d59a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d59a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d59a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d59a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d59a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="2d59a-107">pro Popisovač k oddílu, který má být získán.</span><span class="sxs-lookup"><span data-stu-id="2d59a-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d59a-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d59a-108">Requirements</span></span>  
 <span data-ttu-id="2d59a-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d59a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d59a-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d59a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d59a-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="2d59a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d59a-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d59a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d59a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d59a-113">See also</span></span>

- [<span data-ttu-id="2d59a-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d59a-114">ICeeGen Interface</span></span>](iceegen-interface.md)
