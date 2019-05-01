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
ms.openlocfilehash: 68fe41afa1999295a32b930b779991e2bbddb19a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042764"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="5e406-102">IMetaDataError::OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="5e406-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="5e406-103">Poskytuje oznámení chyb, k nimž došlo při sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="5e406-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e406-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e406-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e406-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e406-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="5e406-106">[in] Vrátila hodnota HRESULT chyby pro volání metody.</span><span class="sxs-lookup"><span data-stu-id="5e406-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="5e406-107">[in] Token metadat objektu kód, který byl slučovány, kdy došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="5e406-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e406-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e406-108">Requirements</span></span>  
 <span data-ttu-id="5e406-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e406-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e406-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5e406-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e406-111">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e406-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e406-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e406-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e406-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e406-113">See also</span></span>

- [<span data-ttu-id="5e406-114">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e406-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
