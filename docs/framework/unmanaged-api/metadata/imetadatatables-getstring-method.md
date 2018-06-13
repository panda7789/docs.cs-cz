---
title: IMetaDataTables::GetString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ed3501930b94eae59cf38355f8255ecf4165bcc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449579"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="1bad0-102">IMetaDataTables::GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="1bad0-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="1bad0-103">Získá řetězec v zadaném indexu ze sloupce tabulky v aktuálním oboru odkaz.</span><span class="sxs-lookup"><span data-stu-id="1bad0-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bad0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bad0-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bad0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1bad0-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="1bad0-106">[v] Index, od kterého má začít k vyhledání další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1bad0-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="1bad0-107">[out] Ukazatel na ukazatel na hodnotu vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="1bad0-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bad0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bad0-108">Requirements</span></span>  
 <span data-ttu-id="1bad0-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bad0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bad0-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1bad0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1bad0-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1bad0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1bad0-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bad0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bad0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bad0-113">See Also</span></span>  
 [<span data-ttu-id="1bad0-114">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1bad0-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="1bad0-115">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1bad0-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
