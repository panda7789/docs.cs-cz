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
ms.openlocfilehash: b956ac1717ffcb73e819e985450249754f80af2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777439"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="840fe-102">IMetaDataImport::IsGlobal – metoda</span><span class="sxs-lookup"><span data-stu-id="840fe-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="840fe-103">Získá hodnotu označující, zda pole, metodu nebo typ zastoupený token metadat zadaného má globální obor.</span><span class="sxs-lookup"><span data-stu-id="840fe-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="840fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="840fe-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="840fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="840fe-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="840fe-106">[in] Token metadat, který představuje typ, pole nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="840fe-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="840fe-107">[out] 1, pokud objekt má globální obor; jinak 0 (nula).</span><span class="sxs-lookup"><span data-stu-id="840fe-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="840fe-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="840fe-108">Requirements</span></span>  
 <span data-ttu-id="840fe-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="840fe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="840fe-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="840fe-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="840fe-111">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="840fe-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="840fe-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="840fe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="840fe-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="840fe-113">See also</span></span>

- [<span data-ttu-id="840fe-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="840fe-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="840fe-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="840fe-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
