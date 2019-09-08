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
ms.openlocfilehash: f062f47790136e8cd39c6751b7c75eef660c2b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799136"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="0d213-102">StrongNameKeyGen – funkce</span><span class="sxs-lookup"><span data-stu-id="0d213-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="0d213-103">Vytvoří nový pár veřejného a privátního klíče pro použití se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0d213-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="0d213-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0d213-104">This function has been deprecated.</span></span> <span data-ttu-id="0d213-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyGen –](../hosting/iclrstrongname-strongnamekeygen-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0d213-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d213-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d213-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d213-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d213-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="0d213-108">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="0d213-108">[in] The requested key container name.</span></span> <span data-ttu-id="0d213-109">`wszKeyContainer`aby bylo možné vytvořit dočasný název, musí být neprázdný řetězec nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="0d213-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0d213-110">pro Určuje, jestli se má zaregistrovaný klíč ponechat.</span><span class="sxs-lookup"><span data-stu-id="0d213-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="0d213-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="0d213-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="0d213-112">0x00000000 – používá se `wszKeyContainer` , pokud je null k vygenerování dočasného názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="0d213-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="0d213-113">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="0d213-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="0d213-114">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="0d213-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="0d213-115">mimo Velikost v bajtech `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="0d213-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d213-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0d213-116">Return Value</span></span>  
 <span data-ttu-id="0d213-117">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="0d213-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d213-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d213-118">Remarks</span></span>  
 <span data-ttu-id="0d213-119">`StrongNameKeyGen` Funkce vytvoří 1024 bitový klíč.</span><span class="sxs-lookup"><span data-stu-id="0d213-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="0d213-120">Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="0d213-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="0d213-121">Pokud se `StrongNameKeyGen` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="0d213-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d213-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d213-122">Requirements</span></span>  
 <span data-ttu-id="0d213-123">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d213-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d213-124">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="0d213-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0d213-125">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0d213-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d213-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d213-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d213-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d213-127">See also</span></span>

- [<span data-ttu-id="0d213-128">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="0d213-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="0d213-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="0d213-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="0d213-130">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d213-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
