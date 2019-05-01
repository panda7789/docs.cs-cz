---
title: StrongNameKeyGen – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8ebecce4078ba6c2b59e6bfba2d54300ba0c4ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000256"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="f8a5e-102">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="f8a5e-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="f8a5e-103">Vytvoří nový pár veřejného a privátního klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="f8a5e-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-104">This function has been deprecated.</span></span> <span data-ttu-id="f8a5e-105">Použití [iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a5e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8a5e-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8a5e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8a5e-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="f8a5e-108">[in] Název požadovaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-108">[in] The requested key container name.</span></span> <span data-ttu-id="f8a5e-109">`wszKeyContainer` musí být neprázdný řetězec, nebo null, pokud chcete generovat dočasný název.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f8a5e-110">[in] Určuje, zda má zůstat zkratku zaregistrovanou.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="f8a5e-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="f8a5e-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="f8a5e-112">0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="f8a5e-113">0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="f8a5e-114">[out] Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="f8a5e-115">[out] Velikost v bajtech, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8a5e-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8a5e-116">Return Value</span></span>  
 <span data-ttu-id="f8a5e-117">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8a5e-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8a5e-118">Remarks</span></span>  
 <span data-ttu-id="f8a5e-119">`StrongNameKeyGen` Funkce vytvoří klíče 1 024 bitů.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="f8a5e-120">Po načtení klíče, měli byste zavolat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce přidělená paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f8a5e-121">Pokud `StrongNameKeyGen` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="f8a5e-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8a5e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8a5e-122">Requirements</span></span>  
 <span data-ttu-id="f8a5e-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8a5e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8a5e-124">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f8a5e-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f8a5e-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8a5e-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8a5e-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a5e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a5e-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8a5e-127">See also</span></span>

- [<span data-ttu-id="f8a5e-128">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="f8a5e-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="f8a5e-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f8a5e-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="f8a5e-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8a5e-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
