---
title: IMetaDataImport::GetTypeSpecFromToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54c35f4f7a7f933bbc06a641d9ba00c5059b5ff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448302"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="ac067-102">IMetaDataImport::GetTypeSpecFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ac067-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="ac067-103">Získá podpis binární metadat specifikace typu reprezentována zadaný token.</span><span class="sxs-lookup"><span data-stu-id="ac067-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac067-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac067-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac067-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac067-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="ac067-106">[v] Typ TypeSpec token přidružený k podpisu požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="ac067-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="ac067-107">[out] Ukazatel na binární metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="ac067-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="ac067-108">[out] Velikost v bajtech podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="ac067-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac067-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ac067-109">Return Value</span></span>  
 <span data-ttu-id="ac067-110">HRESULT, která označuje úspěch nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="ac067-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="ac067-111">Selhání může být testována pomocí makro se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="ac067-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac067-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac067-112">Requirements</span></span>  
 <span data-ttu-id="ac067-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac067-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac067-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac067-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac067-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac067-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac067-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac067-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac067-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac067-117">See Also</span></span>  
 [<span data-ttu-id="ac067-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac067-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ac067-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac067-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
