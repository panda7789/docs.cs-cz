---
title: StrongNameKeyDelete – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a35ec4e3c3110616ac20cd31db134371838deda0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461926"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="4010a-102">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="4010a-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="4010a-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="4010a-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="4010a-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="4010a-104">This function has been deprecated.</span></span> <span data-ttu-id="4010a-105">Použití [iclrstrongname::strongnamekeydelete –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="4010a-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4010a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4010a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4010a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4010a-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="4010a-108">[v] Název kontejneru klíčů odstranit.</span><span class="sxs-lookup"><span data-stu-id="4010a-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4010a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4010a-109">Return Value</span></span>  
 <span data-ttu-id="4010a-110">`true` Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="4010a-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4010a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4010a-111">Remarks</span></span>  
 <span data-ttu-id="4010a-112">Použití [strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) funkce importa pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="4010a-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="4010a-113">Pokud `StrongNameKeyDelete` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="4010a-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4010a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4010a-114">Requirements</span></span>  
 <span data-ttu-id="4010a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4010a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4010a-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4010a-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4010a-117">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4010a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4010a-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4010a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4010a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4010a-119">See Also</span></span>  
 [<span data-ttu-id="4010a-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="4010a-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="4010a-121">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="4010a-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="4010a-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4010a-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
