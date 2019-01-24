---
title: IMetaDataError::OnError – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ebb7fdbcf8c17991928df2dc621ec651b9cd4f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678717"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="0164a-102">IMetaDataError::OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="0164a-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="0164a-103">Poskytuje oznámení chyb, k nimž došlo při sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="0164a-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0164a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0164a-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0164a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0164a-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="0164a-106">[in] Vrátila hodnota HRESULT chyby pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="0164a-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="0164a-107">[in] Token metadat objektu kód, který byl slučovány, kdy došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="0164a-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0164a-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0164a-108">Requirements</span></span>  
 <span data-ttu-id="0164a-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0164a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0164a-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0164a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0164a-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0164a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0164a-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0164a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0164a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0164a-113">See also</span></span>
- [<span data-ttu-id="0164a-114">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0164a-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
