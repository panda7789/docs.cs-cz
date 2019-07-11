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
ms.openlocfilehash: 74445b03e78ff68426f60c3e306d9151d0ba288a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780996"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="f6013-102">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="f6013-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="f6013-103">Vytvoří nový pár veřejného a privátního klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f6013-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="f6013-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f6013-104">This function has been deprecated.</span></span> <span data-ttu-id="f6013-105">Použití [iclrstrongname::strongnamekeygen –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="f6013-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6013-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6013-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6013-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6013-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="f6013-108">[in] Název požadovaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="f6013-108">[in] The requested key container name.</span></span> <span data-ttu-id="f6013-109">`wszKeyContainer` musí být neprázdný řetězec, nebo null, pokud chcete generovat dočasný název.</span><span class="sxs-lookup"><span data-stu-id="f6013-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f6013-110">[in] Určuje, zda má zůstat zkratku zaregistrovanou.</span><span class="sxs-lookup"><span data-stu-id="f6013-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="f6013-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="f6013-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="f6013-112">0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="f6013-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="f6013-113">0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="f6013-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="f6013-114">[out] Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="f6013-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="f6013-115">[out] Velikost v bajtech, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f6013-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6013-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6013-116">Return Value</span></span>  
 <span data-ttu-id="f6013-117">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f6013-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6013-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6013-118">Remarks</span></span>  
 <span data-ttu-id="f6013-119">`StrongNameKeyGen` Funkce vytvoří klíče 1 024 bitů.</span><span class="sxs-lookup"><span data-stu-id="f6013-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="f6013-120">Po načtení klíče, měli byste zavolat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce přidělená paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="f6013-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f6013-121">Pokud `StrongNameKeyGen` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="f6013-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6013-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6013-122">Requirements</span></span>  
 <span data-ttu-id="f6013-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6013-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6013-124">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f6013-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f6013-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6013-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6013-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6013-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6013-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6013-127">See also</span></span>

- [<span data-ttu-id="f6013-128">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="f6013-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="f6013-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f6013-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="f6013-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6013-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
