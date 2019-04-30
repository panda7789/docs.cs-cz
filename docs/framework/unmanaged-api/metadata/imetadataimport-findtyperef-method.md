---
title: IMetaDataImport::FindTypeRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acc006894f05536ed76bac60b0fde9277a460813
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777842"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="75893-102">IMetaDataImport::FindTypeRef – metoda</span><span class="sxs-lookup"><span data-stu-id="75893-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="75893-103">Získá ukazatel Odkaz TypeRef token pro <xref:System.Type> odkaz, který je v zadaném oboru a který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="75893-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75893-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75893-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75893-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75893-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="75893-106">[in] Odkaz ModuleRef, odkaz AssemblyRef ani TypeRef token, který určuje modul, sestavení nebo typ, v uvedeném pořadí, ve které odkazují na typ je definován.</span><span class="sxs-lookup"><span data-stu-id="75893-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="75893-107">[in] Název typu odkazu na hledání.</span><span class="sxs-lookup"><span data-stu-id="75893-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="75893-108">[out] Ukazatel na odpovídající token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="75893-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75893-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75893-109">Requirements</span></span>  
 <span data-ttu-id="75893-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75893-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75893-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75893-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75893-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75893-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75893-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75893-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75893-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75893-114">See also</span></span>

- [<span data-ttu-id="75893-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75893-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="75893-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75893-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
