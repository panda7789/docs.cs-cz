---
title: IMetaDataImport2::GetMethodSpecProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c35212e7d261a5b385823fdaa345f6fbd638571c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959567"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="45b3b-102">IMetaDataImport2::GetMethodSpecProps – metoda</span><span class="sxs-lookup"><span data-stu-id="45b3b-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="45b3b-103">Získá metadata podpis metody odkazuje zadaný token MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="45b3b-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45b3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45b3b-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="45b3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45b3b-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="45b3b-106">[in] Token MethodSpec, který představuje instanci metody.</span><span class="sxs-lookup"><span data-stu-id="45b3b-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="45b3b-107">[out] Ukazatel na token MethodDef nebo MethodRef, který představuje definici metody.</span><span class="sxs-lookup"><span data-stu-id="45b3b-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="45b3b-108">[out] Ukazatel na binární metadat podpis metody.</span><span class="sxs-lookup"><span data-stu-id="45b3b-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="45b3b-109">[out] Velikost v bajtech, z `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="45b3b-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45b3b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45b3b-110">Requirements</span></span>  
 <span data-ttu-id="45b3b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45b3b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45b3b-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="45b3b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45b3b-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45b3b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45b3b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45b3b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45b3b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45b3b-115">See also</span></span>

- [<span data-ttu-id="45b3b-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45b3b-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="45b3b-117">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45b3b-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
