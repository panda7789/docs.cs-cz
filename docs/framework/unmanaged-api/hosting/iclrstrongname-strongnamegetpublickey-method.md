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
ms.openlocfilehash: 943251357a91ea9ae3d492fa7bf20eebf948b8b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135067"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="96f98-102">ICLRStrongName::StrongNameGetPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="96f98-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="96f98-103">Získá veřejný klíč z páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="96f98-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="96f98-104">Pár klíčů je možné zadat buď jako název kontejneru klíčů v rámci zprostředkovatele kryptografických služeb (CSP), nebo jako nezpracovaných kolekcí bajtů.</span><span class="sxs-lookup"><span data-stu-id="96f98-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f98-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96f98-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f98-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="96f98-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="96f98-107">pro Název kontejneru klíčů, který obsahuje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="96f98-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="96f98-108">Pokud je `pbKeyBlob` null, musí `szKeyContainer` v rámci CSP určovat platný kontejner.</span><span class="sxs-lookup"><span data-stu-id="96f98-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="96f98-109">V tomto případě metoda [ICLRStrongName:: StrongNameGetPublicKey –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrahuje veřejný klíč z páru klíčů uloženého v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="96f98-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="96f98-110">Pokud `pbKeyBlob` není null, předpokládá se, že dvojice klíčů bude obsažena v binárním velkém objektu (BLOB) klíče.</span><span class="sxs-lookup"><span data-stu-id="96f98-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="96f98-111">Klíče musí být 1024-bit Rivest-Shamir-Adleman (RSA) Signing Keys.</span><span class="sxs-lookup"><span data-stu-id="96f98-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="96f98-112">V tuto chvíli není podporovaný žádný jiný typ klíčů.</span><span class="sxs-lookup"><span data-stu-id="96f98-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="96f98-113">pro Ukazatel na pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="96f98-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="96f98-114">Tato dvojice je ve formátu vytvořeném funkcí Win32 `CryptExportKey`.</span><span class="sxs-lookup"><span data-stu-id="96f98-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="96f98-115">Je-li `pbKeyBlob` null, předpokládá se, že kontejner klíčů určený parametrem `szKeyContainer` obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="96f98-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="96f98-116">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="96f98-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="96f98-117">mimo Vrácený objekt BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="96f98-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="96f98-118">Parametr `ppbPublicKeyBlob` je přidělen modulem CLR (Common Language Runtime) a vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="96f98-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="96f98-119">Volající musí uvolnit paměť pomocí metody [ICLRStrongName:: StrongNameFreeBuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="96f98-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="96f98-120">mimo Velikost vráceného objektu BLOB veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="96f98-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96f98-121">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96f98-121">Return Value</span></span>  
 <span data-ttu-id="96f98-122">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="96f98-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f98-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96f98-123">Remarks</span></span>  
 <span data-ttu-id="96f98-124">Veřejný klíč je obsažen ve struktuře [PublicKeyBlob –](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="96f98-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f98-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96f98-125">Requirements</span></span>  
 <span data-ttu-id="96f98-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96f98-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f98-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="96f98-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="96f98-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96f98-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96f98-129">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f98-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f98-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96f98-130">See also</span></span>

- [<span data-ttu-id="96f98-131">StrongNameTokenFromPublicKey – metoda</span><span class="sxs-lookup"><span data-stu-id="96f98-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="96f98-132">PublicKeyBlob – struktura</span><span class="sxs-lookup"><span data-stu-id="96f98-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="96f98-133">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96f98-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
