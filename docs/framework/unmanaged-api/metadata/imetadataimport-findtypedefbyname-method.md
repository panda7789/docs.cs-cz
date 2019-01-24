---
title: IMetaDataImport::FindTypeDefByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b6040f21bb530ce775fc79e33b97eb14870c04f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578811"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="50376-102">IMetaDataImport::FindTypeDefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="50376-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="50376-103">Získá ukazatel na TypeDef metadata token pro <xref:System.Type> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="50376-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50376-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50376-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50376-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50376-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="50376-106">[in] Název typu, pro které chcete získat token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="50376-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="50376-107">[in] Token TypeDef nebo TypeRef představující nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="50376-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="50376-108">Pokud hledaný typ není vnořené třídy, nastavte tuto hodnotu na hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="50376-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="50376-109">[out] Ukazatel na odpovídající token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="50376-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50376-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50376-110">Requirements</span></span>  
 <span data-ttu-id="50376-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50376-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50376-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50376-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50376-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50376-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50376-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50376-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50376-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50376-115">See also</span></span>
- [<span data-ttu-id="50376-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50376-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="50376-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50376-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
