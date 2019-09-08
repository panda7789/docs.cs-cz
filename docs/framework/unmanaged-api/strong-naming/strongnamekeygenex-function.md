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
ms.openlocfilehash: f9ab908866402bd7a883114466f32921321a5ee6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799009"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="8a06e-102">StrongNameKeyGenEx – funkce</span><span class="sxs-lookup"><span data-stu-id="8a06e-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="8a06e-103">Vygeneruje nový pár veřejného a privátního klíče se zadanou velikostí klíče pro použití silného názvu.</span><span class="sxs-lookup"><span data-stu-id="8a06e-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="8a06e-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="8a06e-104">This function has been deprecated.</span></span> <span data-ttu-id="8a06e-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyGenEx –](../hosting/iclrstrongname-strongnamekeygenex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8a06e-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a06e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a06e-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a06e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a06e-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="8a06e-108">pro Požadovaný název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a06e-108">[in] The requested key container name.</span></span> <span data-ttu-id="8a06e-109">`wszKeyContainer`aby bylo možné vytvořit dočasný název, musí být neprázdný řetězec nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="8a06e-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8a06e-110">pro Určuje, jestli se má zaregistrovaný klíč ponechat.</span><span class="sxs-lookup"><span data-stu-id="8a06e-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="8a06e-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="8a06e-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="8a06e-112">0x00000000 – používá se `wszKeyContainer` , pokud je null k vygenerování dočasného názvu kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a06e-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="8a06e-113">0x00000001 (`SN_LEAVE_KEY`) – určuje, že klíč by měl zůstat registrovaný.</span><span class="sxs-lookup"><span data-stu-id="8a06e-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="8a06e-114">pro Požadovaná velikost klíče v bitech.</span><span class="sxs-lookup"><span data-stu-id="8a06e-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="8a06e-115">mimo Vrácený pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="8a06e-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="8a06e-116">mimo Velikost v bajtech `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8a06e-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a06e-117">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8a06e-117">Return Value</span></span>  
 <span data-ttu-id="8a06e-118">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="8a06e-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a06e-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a06e-119">Remarks</span></span>  
 <span data-ttu-id="8a06e-120">.NET Framework verze 1,0 a 1,1 vyžadují `dwKeySize` pro podepsání sestavení silným názvem 1024 bitů. verze 2,0 přidá podporu 2048 pro 64bitové klíče.</span><span class="sxs-lookup"><span data-stu-id="8a06e-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="8a06e-121">Po načtení klíče byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="8a06e-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="8a06e-122">Pokud se `StrongNameKeyGenEx` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="8a06e-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a06e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a06e-123">Requirements</span></span>  
 <span data-ttu-id="8a06e-124">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a06e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a06e-125">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="8a06e-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="8a06e-126">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8a06e-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a06e-127">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a06e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a06e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a06e-128">See also</span></span>

- [<span data-ttu-id="8a06e-129">StrongNameKeyGenEx – metoda</span><span class="sxs-lookup"><span data-stu-id="8a06e-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="8a06e-130">StrongNameKeyGen – metoda</span><span class="sxs-lookup"><span data-stu-id="8a06e-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="8a06e-131">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a06e-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
