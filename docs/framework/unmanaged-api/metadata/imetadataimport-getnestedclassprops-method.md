---
title: IMetaDataImport::GetNestedClassProps – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7dd59c1e0e8b28c557910da3fd9c6489370cc62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778950"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="4fc07-102">IMetaDataImport::GetNestedClassProps – metoda</span><span class="sxs-lookup"><span data-stu-id="4fc07-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="4fc07-103">Získá token TypeDef pro nadřazený <xref:System.Type> zadaného vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="4fc07-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fc07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fc07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fc07-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="4fc07-106">[in] Token TypeDef představitel <xref:System.Type> se vraťte na nadřazenou třídu tokenu pro.</span><span class="sxs-lookup"><span data-stu-id="4fc07-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="4fc07-107">[out] Token TypeDef pro ukazatel <xref:System.Type> , který `tdNestedClass` je vnořená v.</span><span class="sxs-lookup"><span data-stu-id="4fc07-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc07-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fc07-108">Requirements</span></span>  
 <span data-ttu-id="4fc07-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc07-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc07-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4fc07-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fc07-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fc07-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fc07-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc07-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc07-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fc07-113">See also</span></span>

- [<span data-ttu-id="4fc07-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fc07-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4fc07-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fc07-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
