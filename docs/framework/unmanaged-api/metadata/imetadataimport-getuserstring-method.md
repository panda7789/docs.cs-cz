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
ms.openlocfilehash: 358ca84f32e1b233116605bf5486cc9a01b42e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503497"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="89425-102">IMetaDataImport::GetUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="89425-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="89425-103">Získá řetězcový literál reprezentovaný zadaným tokenem metadat.</span><span class="sxs-lookup"><span data-stu-id="89425-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89425-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89425-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89425-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89425-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="89425-106">pro Řetězcový token, pro který má být vrácen přidružený řetězec.</span><span class="sxs-lookup"><span data-stu-id="89425-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="89425-107">mimo Kopie požadovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="89425-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="89425-108">pro Maximální velikost požadovaného typu v různých znacích `szString` .</span><span class="sxs-lookup"><span data-stu-id="89425-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="89425-109">mimo Velikost vrácených znaků v různých znacích `szString` .</span><span class="sxs-lookup"><span data-stu-id="89425-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89425-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89425-110">Requirements</span></span>  
 <span data-ttu-id="89425-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89425-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89425-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89425-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89425-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89425-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89425-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89425-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89425-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89425-115">See also</span></span>

- [<span data-ttu-id="89425-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89425-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="89425-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89425-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
