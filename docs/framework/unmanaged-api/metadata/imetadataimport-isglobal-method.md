---
title: "IMetaDataImport::IsGlobal – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsGlobal
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09f7d437e09063bf621990dec4f2903139af8238
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="c3786-102">IMetaDataImport::IsGlobal – metoda</span><span class="sxs-lookup"><span data-stu-id="c3786-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="c3786-103">Získá hodnotu označující, zda pole, metoda nebo typu představovaný typem Zadaná metadata token má globální obor.</span><span class="sxs-lookup"><span data-stu-id="c3786-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3786-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3786-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3786-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3786-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="c3786-106">[v] Metadata token, který představuje typ, pole nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="c3786-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="c3786-107">[out] 1 Pokud objekt má globální rozsah. jinak hodnota 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="c3786-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3786-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3786-108">Requirements</span></span>  
 <span data-ttu-id="c3786-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3786-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3786-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3786-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3786-111">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3786-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3786-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3786-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3786-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3786-113">See Also</span></span>  
 [<span data-ttu-id="c3786-114">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3786-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c3786-115">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3786-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
