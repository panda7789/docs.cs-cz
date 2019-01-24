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
ms.openlocfilehash: 53d0f3bd991d502e4ddcad7df1e24d18af367e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598391"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="8bc61-102">IMetaDataImport::GetTypeSpecFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="8bc61-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="8bc61-103">Získá metadata binární podpis specifikace typu, který je reprezentován zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="8bc61-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bc61-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bc61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bc61-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="8bc61-106">[in] Token TypeSpec tokenu přidružený k podpisu požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="8bc61-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="8bc61-107">[out] Ukazatel na podpis binárního metadat.</span><span class="sxs-lookup"><span data-stu-id="8bc61-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="8bc61-108">[out] Velikost v bajtech, podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="8bc61-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bc61-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8bc61-109">Return Value</span></span>  
 <span data-ttu-id="8bc61-110">HRESULT, která indikuje úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="8bc61-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="8bc61-111">Chyby lze testovat pomocí – makro se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="8bc61-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc61-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bc61-112">Requirements</span></span>  
 <span data-ttu-id="8bc61-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bc61-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bc61-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8bc61-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bc61-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bc61-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bc61-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bc61-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc61-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bc61-117">See also</span></span>
- [<span data-ttu-id="8bc61-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bc61-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8bc61-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bc61-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
