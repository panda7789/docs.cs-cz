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
ms.openlocfilehash: 79b2235e3645c89c2cd9ebcce079d5eb7efdd162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128743"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="32525-102">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="32525-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="32525-103">Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="32525-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="32525-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="32525-104">This function has been deprecated.</span></span> <span data-ttu-id="32525-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyGen –](../hosting/iclrstrongname-strongnamekeygen-method.md) .</span><span class="sxs-lookup"><span data-stu-id="32525-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32525-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32525-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32525-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="32525-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="32525-108">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="32525-108">[in] The requested key container name.</span></span> <span data-ttu-id="32525-109">`wszKeyContainer` musí být neprázdný řetězec nebo hodnota null, aby se vygeneroval dočasný název.</span><span class="sxs-lookup"><span data-stu-id="32525-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="32525-110">pro Určuje, jestli se má zaregistrovaný klíč ponechat.</span><span class="sxs-lookup"><span data-stu-id="32525-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="32525-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="32525-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="32525-112">0x00000000 – používá se, když `wszKeyContainer` má hodnotu null, aby vygenerovala dočasný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="32525-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="32525-113">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="32525-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="32525-114">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="32525-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="32525-115">mimo Velikost `ppbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="32525-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32525-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="32525-116">Return Value</span></span>  
 <span data-ttu-id="32525-117">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="32525-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32525-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32525-118">Remarks</span></span>  
 <span data-ttu-id="32525-119">Funkce `StrongNameKeyGen` vytvoří 1024 bitový klíč.</span><span class="sxs-lookup"><span data-stu-id="32525-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="32525-120">Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="32525-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="32525-121">Pokud se funkce `StrongNameKeyGen` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="32525-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32525-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32525-122">Requirements</span></span>  
 <span data-ttu-id="32525-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32525-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32525-124">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="32525-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="32525-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="32525-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32525-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32525-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32525-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32525-127">See also</span></span>

- [<span data-ttu-id="32525-128">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="32525-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="32525-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="32525-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="32525-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32525-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
