---
title: "ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff0e51327e0e66c2a282ebf46e6036f81d3d568b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="f1218-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList – metoda</span><span class="sxs-lookup"><span data-stu-id="f1218-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="f1218-103">Získá hodnotu, která určuje, zda zadaný název odpovídá názvu sestavení v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f1218-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1218-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1218-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1218-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1218-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="f1218-106">[v] Název sestavení, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="f1218-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1218-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f1218-107">Return Value</span></span>  
  
|<span data-ttu-id="f1218-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1218-108">HRESULT</span></span>|<span data-ttu-id="f1218-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f1218-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1218-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1218-110">S_OK</span></span>|<span data-ttu-id="f1218-111">Řetězec se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f1218-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="f1218-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f1218-112">S_FALSE</span></span>|<span data-ttu-id="f1218-113">Řetězec v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="f1218-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="f1218-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1218-114">E_FAIL</span></span>|<span data-ttu-id="f1218-115">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f1218-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1218-116">Po návratu E_FAIL metodu modul common language runtime již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f1218-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="f1218-117">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f1218-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1218-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1218-118">Requirements</span></span>  
 <span data-ttu-id="f1218-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1218-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1218-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1218-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1218-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1218-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1218-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1218-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1218-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1218-123">See Also</span></span>  
 [<span data-ttu-id="f1218-124">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1218-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="f1218-125">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1218-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="f1218-126">Ihostassemblymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1218-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="f1218-127">Ihostassemblystore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1218-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
