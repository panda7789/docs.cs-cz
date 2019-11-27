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
ms.openlocfilehash: f10c55abcc044b5bbdbb940001a25f530a4688e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431219"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="7915d-102">IMetaDataError::OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="7915d-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="7915d-103">Poskytuje oznámení o chybách, ke kterým došlo během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="7915d-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7915d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7915d-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7915d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7915d-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="7915d-106">pro Hodnota chyby HRESULT vrácená metodě volání.</span><span class="sxs-lookup"><span data-stu-id="7915d-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="7915d-107">pro Token metadat objektu kódu, který byl sloučen v okamžiku, kdy došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="7915d-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7915d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7915d-108">Requirements</span></span>  
 <span data-ttu-id="7915d-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7915d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7915d-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7915d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7915d-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7915d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7915d-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7915d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7915d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7915d-113">See also</span></span>

- [<span data-ttu-id="7915d-114">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7915d-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
