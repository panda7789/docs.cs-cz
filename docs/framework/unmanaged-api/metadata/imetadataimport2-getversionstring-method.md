---
title: "IMetaDataImport2::GetVersionString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d08f43a790305c960d557064539de680a2d04af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="2034c-102">IMetaDataImport2::GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="2034c-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="2034c-103">Získá číslo verze modulu runtime, který byl použit k vytvoření sestavení.</span><span class="sxs-lookup"><span data-stu-id="2034c-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2034c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2034c-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2034c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2034c-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="2034c-106">[out] Pole pro uložení řetězec, který určuje verzi.</span><span class="sxs-lookup"><span data-stu-id="2034c-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="2034c-107">[v] Velikost v široké znaky z `pwzBuf` pole.</span><span class="sxs-lookup"><span data-stu-id="2034c-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="2034c-108">[out] Počet široké znaky, včetně zakončením hodnotu null, vrátí se v `pwzBuf` pole.</span><span class="sxs-lookup"><span data-stu-id="2034c-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2034c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2034c-109">Remarks</span></span>  
 <span data-ttu-id="2034c-110">`GetVersionString` Metoda získá vytvořené pro verzi aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="2034c-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="2034c-111">Pokud ještě nebyla uložena oboru, nebude mít vytvořené pro verzi a vrátí prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2034c-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2034c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2034c-112">Requirements</span></span>  
 <span data-ttu-id="2034c-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2034c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2034c-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2034c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2034c-115">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2034c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2034c-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2034c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2034c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2034c-117">See Also</span></span>  
 [<span data-ttu-id="2034c-118">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2034c-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="2034c-119">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2034c-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
