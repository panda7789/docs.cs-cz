---
title: StrongNameKeyGenEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77ede995b08aba0822e9d86607e0d1e37bd6f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557328"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="fd23f-102">StrongNameKeyGenEx – funkce</span><span class="sxs-lookup"><span data-stu-id="fd23f-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="fd23f-103">Generuje nový pár veřejného a privátního klíče se zadanou velikost klíče pro použití silným názvem.</span><span class="sxs-lookup"><span data-stu-id="fd23f-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="fd23f-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="fd23f-104">This function has been deprecated.</span></span> <span data-ttu-id="fd23f-105">Použití [iclrstrongname::strongnamekeygenex –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="fd23f-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd23f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd23f-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd23f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd23f-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="fd23f-108">[in] Název požadovaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="fd23f-108">[in] The requested key container name.</span></span> <span data-ttu-id="fd23f-109">`wszKeyContainer` musí být neprázdný řetězec, nebo null, pokud chcete generovat dočasný název.</span><span class="sxs-lookup"><span data-stu-id="fd23f-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fd23f-110">[in] Určuje, zda má zůstat zkratku zaregistrovanou.</span><span class="sxs-lookup"><span data-stu-id="fd23f-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="fd23f-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="fd23f-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="fd23f-112">0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="fd23f-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="fd23f-113">0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="fd23f-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="fd23f-114">[in] Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="fd23f-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="fd23f-115">[out] Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="fd23f-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="fd23f-116">[out] Velikost v bajtech, z `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="fd23f-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd23f-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fd23f-117">Return Value</span></span>  
 <span data-ttu-id="fd23f-118">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="fd23f-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd23f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd23f-119">Remarks</span></span>  
 <span data-ttu-id="fd23f-120">Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` z 1 024 bity k podepisování sestavení silným názvem; přidá verze 2.0 podporuje pro klíče 2048 bitů.</span><span class="sxs-lookup"><span data-stu-id="fd23f-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="fd23f-121">Po načtení klíče, měli byste zavolat [strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkce přidělená paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="fd23f-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="fd23f-122">Pokud `StrongNameKeyGenEx` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="fd23f-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd23f-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd23f-123">Requirements</span></span>  
 <span data-ttu-id="fd23f-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd23f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd23f-125">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="fd23f-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fd23f-126">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd23f-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd23f-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd23f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd23f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd23f-128">See also</span></span>
- [<span data-ttu-id="fd23f-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fd23f-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="fd23f-130">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="fd23f-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="fd23f-131">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd23f-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
