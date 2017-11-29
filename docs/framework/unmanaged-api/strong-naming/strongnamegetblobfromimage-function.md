---
title: "StrongNameGetBlobFromImage – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlobFromImage
helpviewer_keywords: StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 423f874796320d1fbcda2ab642c71b7072642569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="51e92-102">StrongNameGetBlobFromImage – funkce</span><span class="sxs-lookup"><span data-stu-id="51e92-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="51e92-103">Získá binární reprezentace sestavení image na adrese zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="51e92-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="51e92-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="51e92-104">This function has been deprecated.</span></span> <span data-ttu-id="51e92-105">Použití [iclrstrongname::strongnamegetblobfromimage –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="51e92-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e92-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51e92-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51e92-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="51e92-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="51e92-108">[v] Adresa paměti manifest namapované sestavení.</span><span class="sxs-lookup"><span data-stu-id="51e92-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="51e92-109">[v] Velikost v bajtech bitové kopie `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="51e92-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="51e92-110">[v] Vyrovnávací paměť pro obsahovat binární reprezentace bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="51e92-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="51e92-111">[ve out] Požadovanou maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="51e92-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="51e92-112">Po návratu, skutečná velikost v bajtech z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="51e92-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51e92-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51e92-113">Return Value</span></span>  
 <span data-ttu-id="51e92-114">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="51e92-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51e92-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51e92-115">Remarks</span></span>  
 <span data-ttu-id="51e92-116">Pokud `StrongNameGetBlobFromImage` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="51e92-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e92-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51e92-117">Requirements</span></span>  
 <span data-ttu-id="51e92-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51e92-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51e92-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="51e92-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="51e92-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51e92-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51e92-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51e92-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e92-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="51e92-122">See Also</span></span>  
 [<span data-ttu-id="51e92-123">Strongnamegetblobfromimage – metoda</span><span class="sxs-lookup"><span data-stu-id="51e92-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="51e92-124">Strongnamegetblob – metoda</span><span class="sxs-lookup"><span data-stu-id="51e92-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="51e92-125">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51e92-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
