---
title: IMetaDataImport::GetModuleFromScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503580"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="b26f4-102">IMetaDataImport::GetModuleFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="b26f4-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="b26f4-103">Získá token metadat pro modul, na který se odkazuje v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="b26f4-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b26f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b26f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b26f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b26f4-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="b26f4-106">mimo Ukazatel na token představující modul, na který se odkazuje v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="b26f4-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b26f4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b26f4-107">Requirements</span></span>  
 <span data-ttu-id="b26f4-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b26f4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b26f4-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b26f4-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b26f4-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b26f4-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b26f4-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b26f4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26f4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b26f4-112">See also</span></span>

- [<span data-ttu-id="b26f4-113">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b26f4-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b26f4-114">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b26f4-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
