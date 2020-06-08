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
ms.openlocfilehash: 43e9671afa92d36966e51bbdc630db4a9d9083b7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503498"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="46683-102">IMetaDataImport::GetTypeSpecFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="46683-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="46683-103">Získá binární podpis metadat specifikace typu reprezentované zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="46683-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46683-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46683-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46683-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="46683-106">pro Token token TypeSpec přidružený k požadované signatuře metadat</span><span class="sxs-lookup"><span data-stu-id="46683-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="46683-107">mimo Ukazatel na binární podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="46683-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="46683-108">mimo Velikost podpisu metadat v bajtech.</span><span class="sxs-lookup"><span data-stu-id="46683-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46683-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="46683-109">Return Value</span></span>  
 <span data-ttu-id="46683-110">HRESULT, který indikuje úspěch nebo neúspěch.</span><span class="sxs-lookup"><span data-stu-id="46683-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="46683-111">Selhání lze otestovat pomocí makra, které SELHALo.</span><span class="sxs-lookup"><span data-stu-id="46683-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46683-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46683-112">Requirements</span></span>  
 <span data-ttu-id="46683-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46683-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46683-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="46683-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46683-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46683-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46683-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46683-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46683-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46683-117">See also</span></span>

- [<span data-ttu-id="46683-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46683-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="46683-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46683-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
