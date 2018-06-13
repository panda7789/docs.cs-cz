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
ms.openlocfilehash: 1c77f946b14fcb5ddc786488ab42e37eb868fbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448276"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="25f58-102">IMetaDataImport::GetNestedClassProps – metoda</span><span class="sxs-lookup"><span data-stu-id="25f58-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="25f58-103">Získá token TypeDef pro nadřazený prvek <xref:System.Type> zadaného vnořené typu.</span><span class="sxs-lookup"><span data-stu-id="25f58-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25f58-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25f58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25f58-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="25f58-106">[v] TypeDef token reprezentující <xref:System.Type> vrátit nadřazené třídy pro token.</span><span class="sxs-lookup"><span data-stu-id="25f58-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="25f58-107">[out] Ukazatel na token TypeDef pro <xref:System.Type> , `tdNestedClass` vnořen v.</span><span class="sxs-lookup"><span data-stu-id="25f58-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f58-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25f58-108">Requirements</span></span>  
 <span data-ttu-id="25f58-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f58-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f58-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25f58-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25f58-111">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25f58-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25f58-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f58-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f58-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="25f58-113">See Also</span></span>  
 [<span data-ttu-id="25f58-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25f58-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="25f58-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25f58-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
