---
title: "StrongNameKeyDelete – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyDelete
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyDelete
helpviewer_keywords: StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3acd8ae5f330e23642a679962a04ccb4f7e8ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="45cfc-102">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="45cfc-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="45cfc-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="45cfc-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="45cfc-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="45cfc-104">This function has been deprecated.</span></span> <span data-ttu-id="45cfc-105">Použití [iclrstrongname::strongnamekeydelete –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="45cfc-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cfc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45cfc-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45cfc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="45cfc-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="45cfc-108">[v] Název kontejneru klíčů odstranit.</span><span class="sxs-lookup"><span data-stu-id="45cfc-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45cfc-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45cfc-109">Return Value</span></span>  
 <span data-ttu-id="45cfc-110">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="45cfc-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45cfc-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45cfc-111">Remarks</span></span>  
 <span data-ttu-id="45cfc-112">Použití [strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) funkce importa pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="45cfc-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="45cfc-113">Pokud `StrongNameKeyDelete` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="45cfc-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45cfc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45cfc-114">Requirements</span></span>  
 <span data-ttu-id="45cfc-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45cfc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45cfc-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="45cfc-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="45cfc-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45cfc-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45cfc-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45cfc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cfc-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="45cfc-119">See Also</span></span>  
 [<span data-ttu-id="45cfc-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="45cfc-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="45cfc-121">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="45cfc-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="45cfc-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45cfc-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
