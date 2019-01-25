---
title: IMetaDataImport2::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e041efed929255d4ce3af2d051a391bc4179cda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630915"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="601d3-102">IMetaDataImport2::GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="601d3-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="601d3-103">Získá číslo verze modulu runtime, která byla použita k vytvoření sestavení.</span><span class="sxs-lookup"><span data-stu-id="601d3-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="601d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="601d3-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="601d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="601d3-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="601d3-106">[out] Pole pro uložení řetězce, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="601d3-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="601d3-107">[in] Velikost v širokých znaků, z `pwzBuf` pole.</span><span class="sxs-lookup"><span data-stu-id="601d3-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="601d3-108">[out] Vrátí počet širokých znaků, včetně null zakončení, v `pwzBuf` pole.</span><span class="sxs-lookup"><span data-stu-id="601d3-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="601d3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="601d3-109">Remarks</span></span>  
 <span data-ttu-id="601d3-110">`GetVersionString` Metoda získá vytvořené pro verzi aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="601d3-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="601d3-111">Pokud obor nebyl uložen, nebude mít vytvořené pro verzi a bude vrácen prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="601d3-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="601d3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="601d3-112">Requirements</span></span>  
 <span data-ttu-id="601d3-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="601d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="601d3-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="601d3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="601d3-115">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="601d3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="601d3-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="601d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="601d3-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="601d3-117">See also</span></span>
- [<span data-ttu-id="601d3-118">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="601d3-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="601d3-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="601d3-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
