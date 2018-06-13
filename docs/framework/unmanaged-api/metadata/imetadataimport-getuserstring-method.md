---
title: IMetaDataImport::GetUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 474338ff1780ce9b442208cd06f8b14bc411be5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447739"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="c0f2d-102">IMetaDataImport::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="c0f2d-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="c0f2d-103">Získá reprezentována Zadaná metadata token řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="c0f2d-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0f2d-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0f2d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0f2d-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="c0f2d-106">[v] Token řetězec vrátit text přidružený k.</span><span class="sxs-lookup"><span data-stu-id="c0f2d-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="c0f2d-107">[out] Kopie požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0f2d-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c0f2d-108">[v] Maximální velikost v široké znaky požadované `szString`.</span><span class="sxs-lookup"><span data-stu-id="c0f2d-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="c0f2d-109">[out] Velikost v široké znaky vrácený `szString`.</span><span class="sxs-lookup"><span data-stu-id="c0f2d-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0f2d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0f2d-110">Requirements</span></span>  
 <span data-ttu-id="c0f2d-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0f2d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0f2d-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0f2d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0f2d-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0f2d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0f2d-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0f2d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f2d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0f2d-115">See Also</span></span>  
 [<span data-ttu-id="c0f2d-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0f2d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c0f2d-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0f2d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
