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
ms.openlocfilehash: 0bfbfec930c193ea05a01bd5bd9f46d2ec6714b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175288"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="2f218-102">IMetaDataImport2::GetMethodSpecProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2f218-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="2f218-103">Získá podpis metadat metody odkazuje zadaný token MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="2f218-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f218-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f218-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2f218-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f218-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="2f218-106">[v] A MethodSpec token, který představuje instanci metody.</span><span class="sxs-lookup"><span data-stu-id="2f218-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="2f218-107">[out] Ukazatel na token MethodDef nebo MethodRef, který představuje definici metody.</span><span class="sxs-lookup"><span data-stu-id="2f218-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="2f218-108">[out] Ukazatel na podpis binárních metadat metody.</span><span class="sxs-lookup"><span data-stu-id="2f218-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="2f218-109">[out] Velikost v bajtů `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="2f218-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f218-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f218-110">Requirements</span></span>  
 <span data-ttu-id="2f218-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f218-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f218-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="2f218-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f218-113">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f218-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f218-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f218-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f218-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f218-115">See also</span></span>

- [<span data-ttu-id="2f218-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f218-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="2f218-117">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f218-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
