---
title: StrongNameKeyDelete – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364512"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="e0b3a-102">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="e0b3a-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="e0b3a-103">Odstraní zadaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-103">Deletes the specified key container.</span></span>

<span data-ttu-id="e0b3a-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-104">This function has been deprecated.</span></span> <span data-ttu-id="e0b3a-105">Použití [iclrstrongname::strongnamekeydelete –](../hosting/iclrstrongname-strongnamekeydelete-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0b3a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0b3a-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="e0b3a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0b3a-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="e0b3a-108">[in] Název kontejneru klíčů pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0b3a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0b3a-109">Return Value</span></span>

<span data-ttu-id="e0b3a-110">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0b3a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0b3a-111">Remarks</span></span>

<span data-ttu-id="e0b3a-112">Použití [strongnamekeyinstall –](strongnamekeyinstall-function.md) k importu pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="e0b3a-113">Pokud `StrongNameKeyDelete` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="e0b3a-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0b3a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0b3a-114">Requirements</span></span>

<span data-ttu-id="e0b3a-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0b3a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e0b3a-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e0b3a-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="e0b3a-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0b3a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="e0b3a-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b3a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e0b3a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0b3a-119">See also</span></span>

- [<span data-ttu-id="e0b3a-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="e0b3a-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="e0b3a-121">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="e0b3a-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="e0b3a-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0b3a-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)