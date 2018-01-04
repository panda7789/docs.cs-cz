---
title: "IMetaDataImport::FindTypeDefByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeDefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 036a177e807a2ab77a6afa74c7b811eeaaebfd29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="0c0a6-102">IMetaDataImport::FindTypeDefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="0c0a6-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="0c0a6-103">Získá ukazatel k metadatům TypeDef token pro <xref:System.Type> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="0c0a6-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c0a6-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c0a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c0a6-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="0c0a6-106">[v] Název typu, pro které chcete získat token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="0c0a6-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="0c0a6-107">[v] TypeDef nebo Odkaz TypeRef token představující nadřazených tříd.</span><span class="sxs-lookup"><span data-stu-id="0c0a6-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="0c0a6-108">Hledaný typ není vnořené třídy, nastavte tuto hodnotu na NULL.</span><span class="sxs-lookup"><span data-stu-id="0c0a6-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0c0a6-109">[out] Ukazatel na odpovídající TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="0c0a6-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c0a6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c0a6-110">Requirements</span></span>  
 <span data-ttu-id="0c0a6-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c0a6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c0a6-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c0a6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c0a6-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c0a6-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c0a6-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c0a6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0a6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c0a6-115">See Also</span></span>  
 [<span data-ttu-id="0c0a6-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c0a6-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0c0a6-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c0a6-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
