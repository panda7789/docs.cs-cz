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
ms.openlocfilehash: 21a69d120cc732ca6659f77abc9f8ea0c993271e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437784"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="dbdb6-102">IMetaDataImport::FindTypeRef – metoda</span><span class="sxs-lookup"><span data-stu-id="dbdb6-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="dbdb6-103">Získá ukazatel na token TypeRef pro odkaz <xref:System.Type>, který se nachází v zadaném oboru a který má zadaný název.</span><span class="sxs-lookup"><span data-stu-id="dbdb6-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbdb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbdb6-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbdb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbdb6-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="dbdb6-106">pro Token Odkaz ModuleRef, AssemblyRef nebo TypeRef, který určuje modul, sestavení nebo typ v uvedeném pořadí, v němž je definován odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="dbdb6-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="dbdb6-107">pro Název odkazu na typ, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="dbdb6-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="dbdb6-108">mimo Ukazatel na shodný token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="dbdb6-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbdb6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbdb6-109">Requirements</span></span>  
 <span data-ttu-id="dbdb6-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbdb6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbdb6-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dbdb6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dbdb6-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dbdb6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dbdb6-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbdb6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbdb6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbdb6-114">See also</span></span>

- [<span data-ttu-id="dbdb6-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbdb6-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dbdb6-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbdb6-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
