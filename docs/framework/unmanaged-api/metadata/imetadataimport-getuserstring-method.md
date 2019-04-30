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
ms.openlocfilehash: 358346af540c8b6b7ee1523e763bebbacf8cd2bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777517"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="00be3-102">IMetaDataImport::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="00be3-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="00be3-103">Získá reprezentována token metadat zadaného řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="00be3-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00be3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00be3-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00be3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00be3-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="00be3-106">[in] Řetězec s tokenem pro vrácení přidružené řetězce pro.</span><span class="sxs-lookup"><span data-stu-id="00be3-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="00be3-107">[out] Kopie požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="00be3-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="00be3-108">[in] Maximální velikost v širokých znaků požadovaných `szString`.</span><span class="sxs-lookup"><span data-stu-id="00be3-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="00be3-109">[out] Velikost v široké znaky vráceného `szString`.</span><span class="sxs-lookup"><span data-stu-id="00be3-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00be3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00be3-110">Requirements</span></span>  
 <span data-ttu-id="00be3-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00be3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00be3-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00be3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00be3-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00be3-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00be3-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00be3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00be3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00be3-115">See also</span></span>

- [<span data-ttu-id="00be3-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00be3-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="00be3-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00be3-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
