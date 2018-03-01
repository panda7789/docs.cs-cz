---
title: "StrongNameGetBlobFromImage – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3dd5fa1838517baa97079f5d7f75a789384255a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="2ff52-102">StrongNameGetBlobFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="2ff52-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="2ff52-103">Získá binární reprezentace sestavení image na adrese zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="2ff52-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="2ff52-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="2ff52-104">This function has been deprecated.</span></span> <span data-ttu-id="2ff52-105">Použití [iclrstrongname::strongnamegetblobfromimage –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="2ff52-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff52-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ff52-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ff52-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff52-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="2ff52-108">[v] Adresa paměti manifest namapované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2ff52-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2ff52-109">[v] Velikost v bajtech bitové kopie `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="2ff52-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="2ff52-110">[v] Vyrovnávací paměť pro obsahovat binární reprezentace bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="2ff52-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="2ff52-111">[ve out] Požadovanou maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="2ff52-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="2ff52-112">Po návratu, skutečná velikost v bajtech z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="2ff52-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ff52-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ff52-113">Return Value</span></span>  
 <span data-ttu-id="2ff52-114">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="2ff52-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff52-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ff52-115">Remarks</span></span>  
 <span data-ttu-id="2ff52-116">Pokud `StrongNameGetBlobFromImage` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="2ff52-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff52-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ff52-117">Requirements</span></span>  
 <span data-ttu-id="2ff52-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff52-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff52-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2ff52-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2ff52-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ff52-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ff52-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff52-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff52-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff52-122">See Also</span></span>  
 [<span data-ttu-id="2ff52-123">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff52-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="2ff52-124">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff52-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="2ff52-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff52-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
