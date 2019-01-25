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
ms.openlocfilehash: ecd52fce8033876f0599fa0ba25fae0850c0e01f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508482"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="29e37-102">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="29e37-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="29e37-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="29e37-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="29e37-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="29e37-104">This function has been deprecated.</span></span> <span data-ttu-id="29e37-105">Použití [iclrstrongname::strongnamekeyinstall –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="29e37-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e37-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29e37-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29e37-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="29e37-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="29e37-108">[in] Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="29e37-108">[in] The name of the key container.</span></span> <span data-ttu-id="29e37-109">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="29e37-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="29e37-110">[in] Binární pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="29e37-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="29e37-111">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="29e37-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29e37-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="29e37-112">Return Value</span></span>  
 <span data-ttu-id="29e37-113">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="29e37-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29e37-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29e37-114">Remarks</span></span>  
 <span data-ttu-id="29e37-115">Použití [strongnamekeydelete –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) funkce pro odstranění kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="29e37-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="29e37-116">Pokud `StrongNameKeyInstall` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="29e37-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29e37-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29e37-117">Requirements</span></span>  
 <span data-ttu-id="29e37-118">**Platformy:** WindSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29e37-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e37-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="29e37-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="29e37-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29e37-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29e37-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e37-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e37-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29e37-122">See also</span></span>
- [<span data-ttu-id="29e37-123">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="29e37-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="29e37-124">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="29e37-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="29e37-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29e37-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
