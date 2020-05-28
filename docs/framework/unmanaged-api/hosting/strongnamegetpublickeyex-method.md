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
ms.openlocfilehash: 1904a98f254a988ce035847a4cdeede182aa07bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006369"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="a8c92-102">StrongNameGetPublicKeyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="a8c92-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="a8c92-103">Získá veřejný klíč z páru veřejného a privátního klíče a určí algoritmus hash a algoritmus podpisu.</span><span class="sxs-lookup"><span data-stu-id="a8c92-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8c92-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a8c92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8c92-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="a8c92-106">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="a8c92-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="a8c92-107">Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musí určovat platný kontejner v rámci zprostředkovatele kryptografických služeb (CSP).</span><span class="sxs-lookup"><span data-stu-id="a8c92-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="a8c92-108">V tomto případě `StrongNameGetPublicKeyEx` Metoda extrahuje veřejný klíč z páru klíčů, který je uložený v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a8c92-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="a8c92-109">Pokud hodnota `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="a8c92-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a8c92-110">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="a8c92-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a8c92-111">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="a8c92-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a8c92-112">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="a8c92-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a8c92-113">Tato dvojice je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="a8c92-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a8c92-114">Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="a8c92-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a8c92-115">pro Velikost v bajtech `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="a8c92-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="a8c92-116">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="a8c92-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="a8c92-117">`ppbPublicKeyBlob`Parametr je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="a8c92-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="a8c92-118">Volající musí uvolnit paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8c92-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="a8c92-119">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="a8c92-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="a8c92-120">pro Algoritmus hash sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8c92-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="a8c92-121">Seznam přijatelných hodnot naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="a8c92-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="a8c92-122">pro Vyhrazeno pro budoucí použití; Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="a8c92-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8c92-123">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8c92-123">Return Value</span></span>  
 <span data-ttu-id="a8c92-124">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="a8c92-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8c92-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8c92-125">Remarks</span></span>  
 <span data-ttu-id="a8c92-126">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="a8c92-126">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8c92-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8c92-127">Remarks</span></span>  
 <span data-ttu-id="a8c92-128">Následující tabulka ukazuje sadu přijatelných hodnot `uHashAlgId` parametru.</span><span class="sxs-lookup"><span data-stu-id="a8c92-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="a8c92-129">Name</span><span class="sxs-lookup"><span data-stu-id="a8c92-129">Name</span></span>|<span data-ttu-id="a8c92-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a8c92-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="a8c92-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8c92-131">None</span></span>|<span data-ttu-id="a8c92-132">0</span><span class="sxs-lookup"><span data-stu-id="a8c92-132">0</span></span>|  
|<span data-ttu-id="a8c92-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="a8c92-133">SHA-1</span></span>|<span data-ttu-id="a8c92-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="a8c92-134">0x8004</span></span>|  
|<span data-ttu-id="a8c92-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="a8c92-135">SHA-256</span></span>|<span data-ttu-id="a8c92-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="a8c92-136">0x800c</span></span>|  
|<span data-ttu-id="a8c92-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="a8c92-137">SHA-384</span></span>|<span data-ttu-id="a8c92-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="a8c92-138">0x800d</span></span>|  
|<span data-ttu-id="a8c92-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="a8c92-139">SHA-512</span></span>|<span data-ttu-id="a8c92-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="a8c92-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8c92-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8c92-141">Requirements</span></span>  
 <span data-ttu-id="a8c92-142">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c92-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c92-143">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a8c92-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a8c92-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8c92-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8c92-145">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c92-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c92-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8c92-146">See also</span></span>

- [<span data-ttu-id="a8c92-147">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="a8c92-147">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="a8c92-148">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="a8c92-148">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="a8c92-149">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8c92-149">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
- [<span data-ttu-id="a8c92-150">StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="a8c92-150">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
