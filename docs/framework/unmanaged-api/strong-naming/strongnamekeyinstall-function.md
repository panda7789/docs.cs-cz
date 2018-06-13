---
title: StrongNameKeyInstall – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b6760a6418533f5c8f6cec815d86b4cff68aab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460077"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="e05c3-102">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="e05c3-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="e05c3-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e05c3-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="e05c3-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e05c3-104">This function has been deprecated.</span></span> <span data-ttu-id="e05c3-105">Použití [iclrstrongname::strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e05c3-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e05c3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e05c3-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e05c3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e05c3-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="e05c3-108">[v] Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="e05c3-108">[in] The name of the key container.</span></span> <span data-ttu-id="e05c3-109">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e05c3-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="e05c3-110">[v] Binární pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="e05c3-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="e05c3-111">[v] Velikost v bajtech z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="e05c3-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e05c3-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e05c3-112">Return Value</span></span>  
 <span data-ttu-id="e05c3-113">`true` Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="e05c3-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e05c3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e05c3-114">Remarks</span></span>  
 <span data-ttu-id="e05c3-115">Použití [strongnamekeydelete –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) funkce odstranit kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="e05c3-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="e05c3-116">Pokud `StrongNameKeyInstall` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="e05c3-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e05c3-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e05c3-117">Requirements</span></span>  
 <span data-ttu-id="e05c3-118">**Platformy:** WindSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e05c3-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e05c3-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e05c3-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e05c3-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e05c3-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e05c3-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e05c3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05c3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e05c3-122">See Also</span></span>  
 [<span data-ttu-id="e05c3-123">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="e05c3-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="e05c3-124">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="e05c3-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="e05c3-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e05c3-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
