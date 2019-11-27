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
ms.openlocfilehash: 8a5dda5861343865a139f6b6b9e2794179b0727a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434726"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="1f4ee-102">IMetaDataImport::IsGlobal – metoda</span><span class="sxs-lookup"><span data-stu-id="1f4ee-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="1f4ee-103">Získá hodnotu, která označuje, zda pole, metoda nebo typ reprezentovaný zadaným tokenem metadat má globální rozsah.</span><span class="sxs-lookup"><span data-stu-id="1f4ee-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f4ee-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f4ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f4ee-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="1f4ee-106">pro Token metadat, který představuje typ, pole nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="1f4ee-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="1f4ee-107">[out] 1, pokud má objekt globální rozsah; v opačném případě 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="1f4ee-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f4ee-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f4ee-108">Requirements</span></span>  
 <span data-ttu-id="1f4ee-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f4ee-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f4ee-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1f4ee-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f4ee-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1f4ee-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f4ee-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f4ee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4ee-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f4ee-113">See also</span></span>

- [<span data-ttu-id="1f4ee-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f4ee-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1f4ee-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f4ee-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
