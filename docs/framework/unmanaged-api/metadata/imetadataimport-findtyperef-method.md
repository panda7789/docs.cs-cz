---
title: "IMetaDataImport::FindTypeRef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d742033788e270f01ee0cea70569ca65e7f35697
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="4d536-102">IMetaDataImport::FindTypeRef – metoda</span><span class="sxs-lookup"><span data-stu-id="4d536-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="4d536-103">Získá ukazatel Odkaz TypeRef tokenu pro <xref:System.Type> odkaz, který se v zadaném oboru a který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="4d536-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d536-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d536-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d536-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="4d536-106">[v] Odkaz ModuleRef, odkaz AssemblyRef nebo Odkaz TypeRef token, který určuje sestavení, modul nebo typ, v uvedeném pořadí, ve kterém odkazovat na typ je definována.</span><span class="sxs-lookup"><span data-stu-id="4d536-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="4d536-107">[v] Název odkaz na typ pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="4d536-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="4d536-108">[out] Ukazatel na odpovídající odkaz TypeRef token.</span><span class="sxs-lookup"><span data-stu-id="4d536-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d536-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d536-109">Requirements</span></span>  
 <span data-ttu-id="4d536-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d536-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d536-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d536-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d536-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d536-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d536-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d536-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d536-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d536-114">See Also</span></span>  
 [<span data-ttu-id="4d536-115">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d536-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4d536-116">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d536-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
