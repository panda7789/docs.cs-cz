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
ms.openlocfilehash: 489fa217744e41ccb5d27d088790131c15e1ee52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177402"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="7a924-102">IMetaDataError::OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="7a924-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="7a924-103">Poskytuje oznámení o chybách, ke kterým dochází během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="7a924-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a924-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a924-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a924-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a924-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="7a924-106">[v] Hodnota chyby HRESULT vrácená volající metodě.</span><span class="sxs-lookup"><span data-stu-id="7a924-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="7a924-107">[v] Token metadat objektu kódu, který byl sloučen, když došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="7a924-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a924-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a924-108">Requirements</span></span>  
 <span data-ttu-id="7a924-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a924-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a924-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="7a924-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a924-111">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a924-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a924-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a924-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a924-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a924-113">See also</span></span>

- [<span data-ttu-id="7a924-114">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a924-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
