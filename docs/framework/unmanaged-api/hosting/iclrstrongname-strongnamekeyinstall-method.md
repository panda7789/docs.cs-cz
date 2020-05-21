---
title: ICLRStrongName::StrongNameKeyInstall – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: e0c60d6e74c48531a223f6dbb35125b5a2017cbb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763035"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="17d98-102">ICLRStrongName::StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="17d98-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="17d98-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="17d98-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17d98-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17d98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17d98-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="17d98-106">pro Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="17d98-106">[in] The name of the key container.</span></span> <span data-ttu-id="17d98-107">`wszKeyContainer`musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="17d98-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="17d98-108">pro Dvojice binárních klíčů.</span><span class="sxs-lookup"><span data-stu-id="17d98-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="17d98-109">pro Velikost v bajtech `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="17d98-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17d98-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="17d98-110">Return Value</span></span>  
 <span data-ttu-id="17d98-111">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="17d98-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d98-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17d98-112">Remarks</span></span>  
 <span data-ttu-id="17d98-113">K odstranění kontejneru klíčů použijte metodu [ICLRStrongName:: StrongNameKeyDelete –](iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17d98-113">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d98-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17d98-114">Requirements</span></span>  
 <span data-ttu-id="17d98-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17d98-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d98-116">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="17d98-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="17d98-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17d98-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17d98-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d98-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d98-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="17d98-119">See also</span></span>

- [<span data-ttu-id="17d98-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="17d98-120">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="17d98-121">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17d98-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
