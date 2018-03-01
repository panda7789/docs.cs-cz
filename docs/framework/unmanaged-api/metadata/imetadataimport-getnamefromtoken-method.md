---
title: "IMetaDataImport::GetNameFromToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: baa0c0e78f7912561b432effd2bf5503e0f06ae7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="28bd8-102">IMetaDataImport::GetNameFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="28bd8-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="28bd8-103">Získá název znakové sady UTF-8 objektu odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="28bd8-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="28bd8-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="28bd8-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28bd8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28bd8-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28bd8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="28bd8-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="28bd8-107">[v] Token představující objekt, který chcete vrátit pro název.</span><span class="sxs-lookup"><span data-stu-id="28bd8-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="28bd8-108">[out] Ukazatel na název objektu UTF-8 v haldě.</span><span class="sxs-lookup"><span data-stu-id="28bd8-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28bd8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28bd8-109">Remarks</span></span>  
 <span data-ttu-id="28bd8-110">`GetNameFromToken`je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="28bd8-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="28bd8-111">Jako alternativu, volejte metodu k získání vlastností konkrétní typ tokenu požadované, například `GetFieldProps` pro pole nebo `GetMethodProps` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="28bd8-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28bd8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28bd8-112">Requirements</span></span>  
 <span data-ttu-id="28bd8-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28bd8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28bd8-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="28bd8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="28bd8-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28bd8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28bd8-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="28bd8-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bd8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="28bd8-117">See Also</span></span>  
 [<span data-ttu-id="28bd8-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28bd8-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="28bd8-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28bd8-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
