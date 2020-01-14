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
ms.openlocfilehash: 834292192aa447a113372bc8807041954b39a115
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937775"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="b8130-102">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="b8130-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="b8130-103">Získá veřejný klíč z páru veřejného a privátního klíče a určí algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="b8130-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8130-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b8130-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8130-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="b8130-106">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="b8130-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="b8130-107">Pokud má `pbKeyBlob` hodnotu null, musí `szKeyContainer` zadat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="b8130-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b8130-108">V tomto případě metoda `StrongNameGetPublicKeyEx` extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="b8130-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="b8130-109">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="b8130-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="b8130-110">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="b8130-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="b8130-111">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="b8130-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b8130-112">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="b8130-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b8130-113">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`.</span><span class="sxs-lookup"><span data-stu-id="b8130-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b8130-114">Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="b8130-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b8130-115">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="b8130-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="b8130-116">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="b8130-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="b8130-117">Parametr `ppbPublicKeyBlob` je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b8130-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="b8130-118">Volající musí uvolnit paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b8130-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="b8130-119">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="b8130-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="b8130-120">pro Algoritmus hash sestavení.</span><span class="sxs-lookup"><span data-stu-id="b8130-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="b8130-121">Seznam přijatelných hodnot naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="b8130-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="b8130-122">pro Vyhrazeno pro budoucí použití; Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="b8130-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8130-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b8130-123">Return Value</span></span>  
 <span data-ttu-id="b8130-124">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="b8130-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8130-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8130-125">Remarks</span></span>  
 <span data-ttu-id="b8130-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="b8130-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8130-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8130-127">Remarks</span></span>  
 <span data-ttu-id="b8130-128">Následující tabulka uvádí sadu přijatelných hodnot parametru `uHashAlgId`.</span><span class="sxs-lookup"><span data-stu-id="b8130-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="b8130-129">Name</span><span class="sxs-lookup"><span data-stu-id="b8130-129">Name</span></span>|<span data-ttu-id="b8130-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b8130-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b8130-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8130-131">None</span></span>|<span data-ttu-id="b8130-132">0</span><span class="sxs-lookup"><span data-stu-id="b8130-132">0</span></span>|  
|<span data-ttu-id="b8130-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="b8130-133">SHA-1</span></span>|<span data-ttu-id="b8130-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="b8130-134">0x8004</span></span>|  
|<span data-ttu-id="b8130-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="b8130-135">SHA-256</span></span>|<span data-ttu-id="b8130-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="b8130-136">0x800c</span></span>|  
|<span data-ttu-id="b8130-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="b8130-137">SHA-384</span></span>|<span data-ttu-id="b8130-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="b8130-138">0x800d</span></span>|  
|<span data-ttu-id="b8130-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="b8130-139">SHA-512</span></span>|<span data-ttu-id="b8130-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="b8130-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8130-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8130-141">Requirements</span></span>  
 <span data-ttu-id="b8130-142">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8130-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8130-143">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b8130-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b8130-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b8130-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8130-145">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8130-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8130-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8130-146">See also</span></span>

- [<span data-ttu-id="b8130-147">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="b8130-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="b8130-148">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="b8130-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="b8130-149">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8130-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="b8130-150">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="b8130-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
