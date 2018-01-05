---
title: "IMetaDataImport::GetTypeSpecFromToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeSpecFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10d4d9dcad2494410cc361617d5292c519b6dc00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="f4e00-102">IMetaDataImport::GetTypeSpecFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="f4e00-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="f4e00-103">Získá podpis binární metadat specifikace typu reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="f4e00-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4e00-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4e00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4e00-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="f4e00-106">[v] Typ TypeSpec token přidružený k podpisu požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="f4e00-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="f4e00-107">[out] Ukazatel na binární metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="f4e00-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="f4e00-108">[out] Velikost v bajtech podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="f4e00-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4e00-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f4e00-109">Return Value</span></span>  
 <span data-ttu-id="f4e00-110">HRESULT, která označuje úspěch nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="f4e00-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="f4e00-111">Selhání může být testována pomocí makro se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="f4e00-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e00-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4e00-112">Requirements</span></span>  
 <span data-ttu-id="f4e00-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4e00-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e00-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4e00-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4e00-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4e00-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4e00-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e00-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e00-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4e00-117">See Also</span></span>  
 [<span data-ttu-id="f4e00-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4e00-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f4e00-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4e00-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
