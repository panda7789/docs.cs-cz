---
title: "IMetaDataImport::GetUserString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 340d5cdfcb218f74a43ed6e88f5175a1d215a1b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="ebbad-102">IMetaDataImport::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="ebbad-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="ebbad-103">Získá reprezentována Zadaná metadata token řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="ebbad-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebbad-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebbad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebbad-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="ebbad-106">[v] Token řetězec vrátit text přidružený k.</span><span class="sxs-lookup"><span data-stu-id="ebbad-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="ebbad-107">[out] Kopie požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ebbad-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="ebbad-108">[v] Maximální velikost v široké znaky požadované `szString`.</span><span class="sxs-lookup"><span data-stu-id="ebbad-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="ebbad-109">[out] Velikost v široké znaky vrácený `szString`.</span><span class="sxs-lookup"><span data-stu-id="ebbad-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbad-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebbad-110">Requirements</span></span>  
 <span data-ttu-id="ebbad-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebbad-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebbad-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ebbad-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebbad-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebbad-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebbad-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebbad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbad-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebbad-115">See Also</span></span>  
 [<span data-ttu-id="ebbad-116">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebbad-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ebbad-117">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ebbad-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
