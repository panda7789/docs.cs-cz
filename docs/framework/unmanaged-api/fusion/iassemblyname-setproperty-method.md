---
title: IAssemblyName::SetProperty – metoda
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17e96f56c57d896397489e27bcc072d8e7df05ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796538"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="eafce-102">IAssemblyName::SetProperty – metoda</span><span class="sxs-lookup"><span data-stu-id="eafce-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="eafce-103">Nastaví hodnotu vlastnosti, na kterou odkazuje zadaný identifikátor vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="eafce-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eafce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eafce-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eafce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eafce-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="eafce-106">pro Jedinečný identifikátor vlastnosti, jejíž hodnota bude nastavena.</span><span class="sxs-lookup"><span data-stu-id="eafce-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="eafce-107">pro Hodnota, na kterou chcete nastavit vlastnost `PropertyId`, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="eafce-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="eafce-108">pro Velikost v bajtech `pvProperty`.</span><span class="sxs-lookup"><span data-stu-id="eafce-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eafce-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eafce-109">Requirements</span></span>  
 <span data-ttu-id="eafce-110">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eafce-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eafce-111">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="eafce-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eafce-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eafce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafce-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eafce-113">See also</span></span>

- [<span data-ttu-id="eafce-114">IAssemblyName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eafce-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
