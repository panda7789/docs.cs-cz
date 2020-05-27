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
ms.openlocfilehash: 79bd8901641ee587e94861c0aec85b812591ea48
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008414"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="9aab2-102">IMetaDataConverter::GetTypeLibFromMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="9aab2-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="9aab2-103">Získá ukazatel na `ITypeLib` instanci, která představuje knihovnu typů, která má zadanou knihovnu a názvy modulů.</span><span class="sxs-lookup"><span data-stu-id="9aab2-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aab2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aab2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aab2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aab2-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="9aab2-106">pro Název modulu knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="9aab2-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="9aab2-107">pro Název knihovny typů</span><span class="sxs-lookup"><span data-stu-id="9aab2-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="9aab2-108">mimo Ukazatel na umístění, které přijímá adresu `ITypeLib` instance, která představuje knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="9aab2-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aab2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9aab2-109">Requirements</span></span>  
 <span data-ttu-id="9aab2-110">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aab2-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aab2-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9aab2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9aab2-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="9aab2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9aab2-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aab2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aab2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9aab2-114">See also</span></span>

- [<span data-ttu-id="9aab2-115">IMetaDataConverter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9aab2-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
