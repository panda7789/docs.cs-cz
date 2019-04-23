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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d77891478c9136a18dc4c9c44beed805244dd1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225934"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="e9607-102">IMetaDataImport::GetNameFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="e9607-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="e9607-103">Získá název kódování UTF-8 odkazuje token metadat zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="e9607-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="e9607-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e9607-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9607-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9607-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9607-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9607-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e9607-107">[in] Token, který představuje objekt, který chcete vrátit pro název.</span><span class="sxs-lookup"><span data-stu-id="e9607-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="e9607-108">[out] Ukazatel na název objektu UTF-8 v haldě.</span><span class="sxs-lookup"><span data-stu-id="e9607-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9607-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9607-109">Remarks</span></span>  
 <span data-ttu-id="e9607-110">`GetNameFromToken` je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="e9607-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="e9607-111">Jako alternativu volat metodu k získání vlastnosti konkrétního typu, jako například vyžaduje se token `GetFieldProps` pro pole nebo `GetMethodProps` pro metodu.</span><span class="sxs-lookup"><span data-stu-id="e9607-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9607-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9607-112">Requirements</span></span>  
 <span data-ttu-id="e9607-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9607-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9607-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e9607-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9607-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9607-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9607-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="e9607-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9607-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9607-117">See also</span></span>

- [<span data-ttu-id="e9607-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9607-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e9607-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9607-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
