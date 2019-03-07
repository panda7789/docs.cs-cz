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
ms.openlocfilehash: 7d610385cfbfcb6a625e0e1893f97525f6f5430c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500600"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="ac56d-102">IMetaDataImport::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="ac56d-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="ac56d-103">Získá reprezentována token metadat zadaného řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="ac56d-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac56d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac56d-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac56d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac56d-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="ac56d-106">[in] Řetězec s tokenem pro vrácení přidružené řetězce pro.</span><span class="sxs-lookup"><span data-stu-id="ac56d-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="ac56d-107">[out] Kopie požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac56d-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="ac56d-108">[in] Maximální velikost v širokých znaků požadovaných `szString`.</span><span class="sxs-lookup"><span data-stu-id="ac56d-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="ac56d-109">[out] Velikost v široké znaky vráceného `szString`.</span><span class="sxs-lookup"><span data-stu-id="ac56d-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac56d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac56d-110">Requirements</span></span>  
 <span data-ttu-id="ac56d-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac56d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac56d-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac56d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac56d-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac56d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac56d-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac56d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac56d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac56d-115">See also</span></span>
- [<span data-ttu-id="ac56d-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac56d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ac56d-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac56d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
