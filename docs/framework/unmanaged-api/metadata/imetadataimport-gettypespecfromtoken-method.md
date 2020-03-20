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
ms.openlocfilehash: 34b7cebfa063a3ad077b74a753fd37ba67ff53a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175314"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="3829b-102">IMetaDataImport::GetTypeSpecFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="3829b-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="3829b-103">Získá podpis binární metadata specifikace typu reprezentované zadaný token.</span><span class="sxs-lookup"><span data-stu-id="3829b-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3829b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3829b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3829b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3829b-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="3829b-106">[v] Token TypeSpec přidružený k požadovanému podpisu metadat.</span><span class="sxs-lookup"><span data-stu-id="3829b-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="3829b-107">[out] Ukazatel na podpis binárních metadat.</span><span class="sxs-lookup"><span data-stu-id="3829b-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="3829b-108">[out] Velikost podpisu metadat v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3829b-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3829b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3829b-109">Return Value</span></span>  
 <span data-ttu-id="3829b-110">HRESULT, který označuje úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="3829b-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="3829b-111">Chyby lze testovat s makro FAILED.</span><span class="sxs-lookup"><span data-stu-id="3829b-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3829b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3829b-112">Requirements</span></span>  
 <span data-ttu-id="3829b-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3829b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3829b-114">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="3829b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3829b-115">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3829b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3829b-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3829b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3829b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3829b-117">See also</span></span>

- [<span data-ttu-id="3829b-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3829b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3829b-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3829b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
