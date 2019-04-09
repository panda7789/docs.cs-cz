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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f40e6bfdbebdadc41da52564348c6070c18372c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194679"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="46579-102">IMetaDataImport::GetModuleFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="46579-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="46579-103">Získá token metadat pro modul odkazovat v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="46579-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46579-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46579-104">Syntax</span></span>  
  
```  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46579-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46579-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="46579-106">[out] Ukazatel na token představující modul odkazovat v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="46579-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46579-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46579-107">Requirements</span></span>  
 <span data-ttu-id="46579-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46579-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46579-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="46579-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46579-110">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46579-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="46579-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="46579-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46579-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46579-112">See also</span></span>

- [<span data-ttu-id="46579-113">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46579-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="46579-114">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46579-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
