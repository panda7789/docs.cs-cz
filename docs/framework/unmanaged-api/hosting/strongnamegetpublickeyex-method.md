---
title: StrongNameGetPublicKeyEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 700bcc5b818c452d3642d325fb6fe19cbb162474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141443"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="16d74-102">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="16d74-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="16d74-103">Získá veřejný klíč z páru veřejného a privátního klíče a určí algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="16d74-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16d74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16d74-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16d74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16d74-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="16d74-106">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="16d74-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="16d74-107">Pokud má `pbKeyBlob` hodnotu null, musí `szKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="16d74-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="16d74-108">V tomto případě metoda `StrongNameGetPublicKeyEx` extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="16d74-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="16d74-109">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="16d74-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="16d74-110">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="16d74-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="16d74-111">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="16d74-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="16d74-112">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="16d74-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="16d74-113">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`.</span><span class="sxs-lookup"><span data-stu-id="16d74-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="16d74-114">Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="16d74-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="16d74-115">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="16d74-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="16d74-116">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="16d74-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="16d74-117">Parametr `ppbPublicKeyBlob` je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="16d74-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="16d74-118">Volající musí uvolnit paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="16d74-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="16d74-119">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="16d74-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="16d74-120">pro Algoritmus hash sestavení.</span><span class="sxs-lookup"><span data-stu-id="16d74-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="16d74-121">Seznam přijatelných hodnot naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="16d74-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="16d74-122">pro Vyhrazeno pro budoucí použití; Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="16d74-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16d74-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="16d74-123">Return Value</span></span>  
 <span data-ttu-id="16d74-124">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="16d74-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16d74-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16d74-125">Remarks</span></span>  
 <span data-ttu-id="16d74-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="16d74-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16d74-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16d74-127">Remarks</span></span>  
 <span data-ttu-id="16d74-128">Následující tabulka uvádí sadu přijatelných hodnot parametru `uHashAlgId`.</span><span class="sxs-lookup"><span data-stu-id="16d74-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="16d74-129">Name</span><span class="sxs-lookup"><span data-stu-id="16d74-129">Name</span></span>|<span data-ttu-id="16d74-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="16d74-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="16d74-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="16d74-131">None</span></span>|<span data-ttu-id="16d74-132">0,8</span><span class="sxs-lookup"><span data-stu-id="16d74-132">0</span></span>|  
|<span data-ttu-id="16d74-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="16d74-133">SHA-1</span></span>|<span data-ttu-id="16d74-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="16d74-134">0x8004</span></span>|  
|<span data-ttu-id="16d74-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="16d74-135">SHA-256</span></span>|<span data-ttu-id="16d74-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="16d74-136">0x800c</span></span>|  
|<span data-ttu-id="16d74-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="16d74-137">SHA-384</span></span>|<span data-ttu-id="16d74-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="16d74-138">0x800d</span></span>|  
|<span data-ttu-id="16d74-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="16d74-139">SHA-512</span></span>|<span data-ttu-id="16d74-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="16d74-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16d74-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16d74-141">Requirements</span></span>  
 <span data-ttu-id="16d74-142">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16d74-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d74-143">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="16d74-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="16d74-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="16d74-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16d74-145">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d74-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d74-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16d74-146">See also</span></span>

- [<span data-ttu-id="16d74-147">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="16d74-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="16d74-148">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="16d74-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="16d74-149">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16d74-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="16d74-150">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="16d74-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
