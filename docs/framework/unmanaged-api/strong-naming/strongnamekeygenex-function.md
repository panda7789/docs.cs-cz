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
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125218"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="aaf2b-102">StrongNameKeyGenEx – funkce</span><span class="sxs-lookup"><span data-stu-id="aaf2b-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="aaf2b-103">Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silného názvu.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="aaf2b-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-104">This function has been deprecated.</span></span> <span data-ttu-id="aaf2b-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyGenEx –](../hosting/iclrstrongname-strongnamekeygenex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aaf2b-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf2b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaf2b-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaf2b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aaf2b-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="aaf2b-108">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-108">[in] The requested key container name.</span></span> <span data-ttu-id="aaf2b-109">`wszKeyContainer` musí být neprázdný řetězec nebo hodnota null, aby se vygeneroval dočasný název.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="aaf2b-110">pro Určuje, jestli se má zaregistrovaný klíč ponechat.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="aaf2b-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="aaf2b-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="aaf2b-112">0x00000000 – používá se, když `wszKeyContainer` má hodnotu null, aby vygenerovala dočasný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="aaf2b-113">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="aaf2b-114">pro Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="aaf2b-115">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="aaf2b-116">mimo Velikost `ppbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf2b-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aaf2b-117">Return Value</span></span>  
 <span data-ttu-id="aaf2b-118">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf2b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaf2b-119">Remarks</span></span>  
 <span data-ttu-id="aaf2b-120">.NET Framework verze 1,0 a 1,1 vyžadují `dwKeySize` 1024 bitů pro podepsání sestavení silným názvem; verze 2,0 přidává podporu pro 2048 bitové klávesy.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="aaf2b-121">Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="aaf2b-122">Pokud se funkce `StrongNameKeyGenEx` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="aaf2b-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaf2b-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aaf2b-123">Requirements</span></span>  
 <span data-ttu-id="aaf2b-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaf2b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaf2b-125">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="aaf2b-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="aaf2b-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aaf2b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aaf2b-127">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaf2b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf2b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaf2b-128">See also</span></span>

- [<span data-ttu-id="aaf2b-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="aaf2b-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="aaf2b-130">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="aaf2b-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="aaf2b-131">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aaf2b-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
