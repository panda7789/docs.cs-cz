---
title: IMetaDataConverter::GetTypeLibFromMetaData – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9351738e979b49ec23b51a2fa554fc219e163541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444113"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="51227-102">IMetaDataConverter::GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="51227-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="51227-103">Získá odkazy `ITypeLib` instanci, která představuje knihovny typů, který má zadané názvy knihovny a modulu.</span><span class="sxs-lookup"><span data-stu-id="51227-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51227-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51227-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51227-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51227-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="51227-106">[v] Název modulu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="51227-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="51227-107">[v] Název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="51227-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="51227-108">[out] Ukazatel na umístění, která přijímá adresu `ITypeLib` instanci, která představuje knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="51227-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51227-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51227-109">Requirements</span></span>  
 <span data-ttu-id="51227-110">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51227-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51227-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51227-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51227-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51227-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51227-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51227-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51227-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="51227-114">See Also</span></span>  
 [<span data-ttu-id="51227-115">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51227-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
