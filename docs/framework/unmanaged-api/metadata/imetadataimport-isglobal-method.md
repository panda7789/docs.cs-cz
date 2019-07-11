---
title: IMetaDataImport::IsGlobal – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13f8a50f3fcbe9d6e7602ca3bbeb36587ecff32c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778797"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="4c9ad-102">IMetaDataImport::IsGlobal – metoda</span><span class="sxs-lookup"><span data-stu-id="4c9ad-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="4c9ad-103">Získá hodnotu označující, zda pole, metodu nebo typ zastoupený token metadat zadaného má globální obor.</span><span class="sxs-lookup"><span data-stu-id="4c9ad-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c9ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c9ad-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c9ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c9ad-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="4c9ad-106">[in] Token metadat, který představuje typ, pole nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="4c9ad-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="4c9ad-107">[out] 1, pokud objekt má globální obor; jinak 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="4c9ad-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c9ad-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c9ad-108">Requirements</span></span>  
 <span data-ttu-id="4c9ad-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c9ad-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c9ad-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c9ad-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c9ad-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c9ad-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c9ad-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c9ad-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9ad-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c9ad-113">See also</span></span>

- [<span data-ttu-id="4c9ad-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c9ad-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4c9ad-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c9ad-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
