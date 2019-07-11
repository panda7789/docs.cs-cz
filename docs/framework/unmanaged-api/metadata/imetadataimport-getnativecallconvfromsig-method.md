---
title: IMetaDataImport::GetNativeCallConvFromSig – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b5dfb31cfe0364a745b729018be536f6be9aac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778966"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="a2b74-102">IMetaDataImport::GetNativeCallConvFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="a2b74-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="a2b74-103">Získá nativní konvence volání pro metodu, která je reprezentována zadaným podpisem ukazatele.</span><span class="sxs-lookup"><span data-stu-id="a2b74-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2b74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2b74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2b74-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="a2b74-106">[in] Ukazatel na podpis metadat k vrácení konvence volání pro metodu.</span><span class="sxs-lookup"><span data-stu-id="a2b74-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="a2b74-107">[in] Velikost v bajtech `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="a2b74-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="a2b74-108">[out] Ukazatel na nativní konvence volání.</span><span class="sxs-lookup"><span data-stu-id="a2b74-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2b74-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2b74-109">Requirements</span></span>  
 <span data-ttu-id="a2b74-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2b74-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2b74-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2b74-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2b74-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2b74-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2b74-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b74-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b74-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2b74-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="a2b74-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2b74-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a2b74-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2b74-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
