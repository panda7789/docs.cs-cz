---
title: IMetaDataImport::IsValidToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d752d6dbe8a6b7a23faae498f9118c8d89e92929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447694"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="f9438-102">IMetaDataImport::IsValidToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f9438-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="f9438-103">Získá hodnotu označující, zda zadaný token obsahuje neplatný odkaz na objekt kódu.</span><span class="sxs-lookup"><span data-stu-id="f9438-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9438-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9438-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9438-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9438-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f9438-106">[v] Token, aby zkontroloval platnost odkazu pro.</span><span class="sxs-lookup"><span data-stu-id="f9438-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9438-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9438-107">Return Value</span></span>  
 <span data-ttu-id="f9438-108">`true` Pokud `tk` je token platný metadata v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="f9438-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="f9438-109">V opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="f9438-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9438-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9438-110">Requirements</span></span>  
 <span data-ttu-id="f9438-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9438-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9438-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f9438-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9438-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f9438-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9438-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9438-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9438-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9438-115">See Also</span></span>  
 [<span data-ttu-id="f9438-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9438-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f9438-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9438-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
