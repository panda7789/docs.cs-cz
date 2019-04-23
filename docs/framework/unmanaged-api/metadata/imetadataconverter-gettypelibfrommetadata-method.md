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
ms.openlocfilehash: c0943971dc4858e2dce4d977f6f906b26f8ad51e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231003"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="83e01-102">IMetaDataConverter::GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="83e01-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="83e01-103">Získá ukazatel `ITypeLib` instanci, která představuje knihovnu typů, který má zadané názvy knihovny a modulu.</span><span class="sxs-lookup"><span data-stu-id="83e01-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e01-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83e01-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="83e01-106">[in] Název knihovny typů modulu.</span><span class="sxs-lookup"><span data-stu-id="83e01-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="83e01-107">[in] Název knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="83e01-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="83e01-108">[out] Ukazatel na umístění, která bude přijímat adresy `ITypeLib` instanci, která představuje knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="83e01-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e01-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83e01-109">Requirements</span></span>  
 <span data-ttu-id="83e01-110">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e01-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e01-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83e01-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83e01-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83e01-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83e01-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e01-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e01-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83e01-114">See also</span></span>

- [<span data-ttu-id="83e01-115">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83e01-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
