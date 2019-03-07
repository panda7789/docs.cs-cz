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
ms.openlocfilehash: 6462496a8804d9aa5304107a6c01122b745038fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500249"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="7754d-102">IMetaDataImport::GetNestedClassProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7754d-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="7754d-103">Získá token TypeDef pro nadřazený <xref:System.Type> zadaného vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="7754d-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7754d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7754d-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7754d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7754d-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="7754d-106">[in] Token TypeDef představitel <xref:System.Type> se vraťte na nadřazenou třídu tokenu pro.</span><span class="sxs-lookup"><span data-stu-id="7754d-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="7754d-107">[out] Token TypeDef pro ukazatel <xref:System.Type> , který `tdNestedClass` je vnořená v.</span><span class="sxs-lookup"><span data-stu-id="7754d-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7754d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7754d-108">Requirements</span></span>  
 <span data-ttu-id="7754d-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7754d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7754d-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7754d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7754d-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7754d-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7754d-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7754d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7754d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7754d-113">See also</span></span>
- [<span data-ttu-id="7754d-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7754d-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7754d-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7754d-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
