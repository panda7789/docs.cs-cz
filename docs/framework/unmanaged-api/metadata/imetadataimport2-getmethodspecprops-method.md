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
ms.openlocfilehash: 3249ad76c428752c91540e135bc978d3fe835de1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448130"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="01f6c-102">IMetaDataImport2::GetMethodSpecProps – metoda</span><span class="sxs-lookup"><span data-stu-id="01f6c-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="01f6c-103">Získá metadata podpis metody odkazuje zadaný MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="01f6c-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01f6c-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="01f6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01f6c-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="01f6c-106">[v] MethodSpec token, který představuje instance metody.</span><span class="sxs-lookup"><span data-stu-id="01f6c-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="01f6c-107">[out] Ukazatel na MethodDef nebo MethodRef token, který představuje definici metody.</span><span class="sxs-lookup"><span data-stu-id="01f6c-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="01f6c-108">[out] Ukazatel na binární metadata podpis metody.</span><span class="sxs-lookup"><span data-stu-id="01f6c-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="01f6c-109">[out] Velikost v bajtech z `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="01f6c-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f6c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01f6c-110">Requirements</span></span>  
 <span data-ttu-id="01f6c-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f6c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f6c-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="01f6c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01f6c-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01f6c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01f6c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f6c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f6c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="01f6c-115">See Also</span></span>  
 [<span data-ttu-id="01f6c-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01f6c-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="01f6c-117">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01f6c-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
