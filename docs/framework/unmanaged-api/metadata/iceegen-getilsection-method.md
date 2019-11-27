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
ms.openlocfilehash: 7ef944fd06d07dc8c4e49061a5e72d8acc4d0465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436343"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="f9e21-102">ICeeGen::GetIlSection – metoda</span><span class="sxs-lookup"><span data-stu-id="f9e21-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="f9e21-103">Získá část základu kódu zprostředkujícího jazyka, na kterou odkazuje zadaný popisovač.</span><span class="sxs-lookup"><span data-stu-id="f9e21-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="f9e21-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="f9e21-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e21-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9e21-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9e21-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9e21-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f9e21-107">pro Popisovač k oddílu, který má být získán.</span><span class="sxs-lookup"><span data-stu-id="f9e21-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e21-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9e21-108">Requirements</span></span>  
 <span data-ttu-id="f9e21-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e21-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e21-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9e21-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9e21-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f9e21-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9e21-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e21-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e21-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9e21-113">See also</span></span>

- [<span data-ttu-id="f9e21-114">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9e21-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
