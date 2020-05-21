---
title: ICLRStrongName::StrongNameKeyDelete – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 8f6f2445d88d608d51be4e6fe1e064efbb58325d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763095"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="c87d0-102">ICLRStrongName::StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="c87d0-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="c87d0-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="c87d0-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c87d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c87d0-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c87d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c87d0-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="c87d0-106">pro Název kontejneru klíčů, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="c87d0-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c87d0-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c87d0-107">Return Value</span></span>  
 <span data-ttu-id="c87d0-108">`S_OK`Pokud byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="c87d0-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c87d0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c87d0-109">Remarks</span></span>  
 <span data-ttu-id="c87d0-110">Pomocí metody [ICLRStrongName:: StrongNameKeyInstall –](iclrstrongname-strongnamekeyinstall-method.md) importujte pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c87d0-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c87d0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c87d0-111">Requirements</span></span>  
 <span data-ttu-id="c87d0-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c87d0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c87d0-113">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c87d0-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c87d0-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c87d0-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c87d0-115">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87d0-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c87d0-116">See also</span></span>

- [<span data-ttu-id="c87d0-117">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="c87d0-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="c87d0-118">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c87d0-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
