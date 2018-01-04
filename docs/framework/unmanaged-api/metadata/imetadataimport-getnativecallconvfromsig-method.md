---
title: "IMetaDataImport::GetNativeCallConvFromSig – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNativeCallConvFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56c67ad76fb3a4ce5ab2d107ff59da7a932835b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="ea31a-102">IMetaDataImport::GetNativeCallConvFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="ea31a-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="ea31a-103">Získá nativního konvence volání pro metodu, která je reprezentována Zadaný podpis ukazatele.</span><span class="sxs-lookup"><span data-stu-id="ea31a-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea31a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea31a-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea31a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea31a-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="ea31a-106">[v] Ukazatel na metadata podpis metody, která vrátí konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="ea31a-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ea31a-107">[v] Velikost v bajtech `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="ea31a-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="ea31a-108">[out] Ukazatel na nativní konvence volání.</span><span class="sxs-lookup"><span data-stu-id="ea31a-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea31a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea31a-109">Requirements</span></span>  
 <span data-ttu-id="ea31a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea31a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea31a-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea31a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea31a-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea31a-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea31a-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea31a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea31a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea31a-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.CallingConvention>  
 [<span data-ttu-id="ea31a-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea31a-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ea31a-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea31a-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
