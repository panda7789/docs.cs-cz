---
title: IMetaDataImport::GetNameFromToken – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 6d62739148280c7333cf7cdb6002b59a145496e3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503559"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="945e2-102">IMetaDataImport::GetNameFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="945e2-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="945e2-103">Získá název UTF-8 objektu, na který odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="945e2-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="945e2-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="945e2-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="945e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="945e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="945e2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="945e2-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="945e2-107">pro Token představující objekt, pro který má být vrácen název.</span><span class="sxs-lookup"><span data-stu-id="945e2-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="945e2-108">mimo Ukazatel na název objektu UTF-8 v haldě.</span><span class="sxs-lookup"><span data-stu-id="945e2-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="945e2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="945e2-109">Remarks</span></span>  
 <span data-ttu-id="945e2-110">`GetNameFromToken`je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="945e2-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="945e2-111">Jako alternativu volejte metodu pro získání vlastností konkrétního typu požadovaného tokenu, například `GetFieldProps` pro pole nebo `GetMethodProps` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="945e2-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="945e2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="945e2-112">Requirements</span></span>  
 <span data-ttu-id="945e2-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="945e2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="945e2-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="945e2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="945e2-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="945e2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="945e2-116">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="945e2-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945e2-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="945e2-117">See also</span></span>

- [<span data-ttu-id="945e2-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="945e2-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="945e2-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="945e2-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
