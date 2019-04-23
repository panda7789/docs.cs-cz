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
ms.openlocfilehash: 362cbe9ff19e74bafc73fde857d231185179efbe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079549"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="13e62-102">IMetaDataImport::GetTypeSpecFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="13e62-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="13e62-103">Získá metadata binární podpis specifikace typu, který je reprezentován zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="13e62-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13e62-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13e62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13e62-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="13e62-106">[in] Token TypeSpec tokenu přidružený k podpisu požadovaná metadata.</span><span class="sxs-lookup"><span data-stu-id="13e62-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="13e62-107">[out] Ukazatel na podpis binárního metadat.</span><span class="sxs-lookup"><span data-stu-id="13e62-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="13e62-108">[out] Velikost v bajtech, podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="13e62-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13e62-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13e62-109">Return Value</span></span>  
 <span data-ttu-id="13e62-110">HRESULT, která indikuje úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="13e62-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="13e62-111">Chyby lze testovat pomocí – makro se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="13e62-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e62-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13e62-112">Requirements</span></span>  
 <span data-ttu-id="13e62-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13e62-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13e62-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13e62-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13e62-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13e62-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13e62-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13e62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e62-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13e62-117">See also</span></span>

- [<span data-ttu-id="13e62-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13e62-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="13e62-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13e62-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
