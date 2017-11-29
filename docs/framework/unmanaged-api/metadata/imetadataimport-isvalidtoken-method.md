---
title: "IMetaDataImport::IsValidToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.IsValidToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c916e71518ded93c90b270205dd975201762846
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="0207e-102">IMetaDataImport::IsValidToken – metoda</span><span class="sxs-lookup"><span data-stu-id="0207e-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="0207e-103">Získá hodnotu označující, zda zadaný token obsahuje neplatný odkaz na objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="0207e-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0207e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0207e-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0207e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0207e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0207e-106">[v] Token, aby zkontroloval platnost odkazu pro.</span><span class="sxs-lookup"><span data-stu-id="0207e-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0207e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0207e-107">Return Value</span></span>  
 <span data-ttu-id="0207e-108">`true`Pokud `tk` je token platný metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="0207e-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="0207e-109">V opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="0207e-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0207e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0207e-110">Requirements</span></span>  
 <span data-ttu-id="0207e-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0207e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0207e-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0207e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0207e-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0207e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0207e-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0207e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0207e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0207e-115">See Also</span></span>  
 [<span data-ttu-id="0207e-116">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0207e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0207e-117">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0207e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
