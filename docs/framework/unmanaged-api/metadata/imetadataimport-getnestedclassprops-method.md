---
title: "IMetaDataImport::GetNestedClassProps – metoda"
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
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8bbfe382a9a2fdf8ece1015ee73c3d9ef604ec7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="80857-102">IMetaDataImport::GetNestedClassProps – metoda</span><span class="sxs-lookup"><span data-stu-id="80857-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="80857-103">Získá token TypeDef pro nadřazený prvek <xref:System.Type> zadaného vnořené typu.</span><span class="sxs-lookup"><span data-stu-id="80857-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80857-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80857-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80857-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80857-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="80857-106">[v] TypeDef token reprezentující <xref:System.Type> vrátit nadřazené třídy pro token.</span><span class="sxs-lookup"><span data-stu-id="80857-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="80857-107">[out] Ukazatel na token TypeDef pro <xref:System.Type> , `tdNestedClass` vnořen v.</span><span class="sxs-lookup"><span data-stu-id="80857-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80857-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80857-108">Requirements</span></span>  
 <span data-ttu-id="80857-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80857-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80857-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80857-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80857-111">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80857-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80857-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80857-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80857-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="80857-113">See Also</span></span>  
 [<span data-ttu-id="80857-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80857-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="80857-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80857-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
