---
title: ICLRStrongName::StrongNameGetPublicKey – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: 5a20bde64830617090c92afe5fae3a603cf9103b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763124"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="93c9b-102">ICLRStrongName::StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="93c9b-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="93c9b-103">Získá veřejný klíč z páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="93c9b-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="93c9b-104">Pár klíčů je možné zadat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP), nebo jako nezpracovaných kolekcí bajtů.</span><span class="sxs-lookup"><span data-stu-id="93c9b-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c9b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c9b-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93c9b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="93c9b-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="93c9b-107">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="93c9b-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="93c9b-108">Pokud `pbKeyBlob` má hodnotu null, `szKeyContainer` musí v rámci CSP určovat platný kontejner.</span><span class="sxs-lookup"><span data-stu-id="93c9b-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="93c9b-109">V tomto případě metoda [ICLRStrongName:: StrongNameGetPublicKey –](iclrstrongname-strongnamegetpublickey-method.md) extrahuje veřejný klíč z páru klíčů uloženého v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="93c9b-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="93c9b-110">Pokud hodnota `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="93c9b-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="93c9b-111">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="93c9b-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="93c9b-112">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="93c9b-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="93c9b-113">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="93c9b-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="93c9b-114">Tato dvojice je ve formátu vytvořeném `CryptExportKey` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="93c9b-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="93c9b-115">Pokud `pbKeyBlob` má hodnotu null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="93c9b-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="93c9b-116">pro Velikost v bajtech `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="93c9b-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="93c9b-117">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="93c9b-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="93c9b-118">`ppbPublicKeyBlob`Parametr je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="93c9b-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="93c9b-119">Volající musí uvolnit paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93c9b-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="93c9b-120">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="93c9b-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93c9b-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93c9b-121">Return Value</span></span>  
 <span data-ttu-id="93c9b-122">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="93c9b-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93c9b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93c9b-123">Remarks</span></span>  
 <span data-ttu-id="93c9b-124">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="93c9b-124">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93c9b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93c9b-125">Requirements</span></span>  
 <span data-ttu-id="93c9b-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93c9b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93c9b-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="93c9b-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="93c9b-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="93c9b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93c9b-129">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93c9b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c9b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="93c9b-130">See also</span></span>

- [<span data-ttu-id="93c9b-131">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="93c9b-131">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="93c9b-132">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="93c9b-132">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="93c9b-133">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93c9b-133">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
