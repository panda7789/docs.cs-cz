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
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636738"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="80d0c-102">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="80d0c-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="80d0c-103">Odstraní zadaný kontejner klíče.</span><span class="sxs-lookup"><span data-stu-id="80d0c-103">Deletes the specified key container.</span></span>

<span data-ttu-id="80d0c-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="80d0c-104">This function has been deprecated.</span></span> <span data-ttu-id="80d0c-105">Použití [iclrstrongname::strongnamekeydelete –](../hosting/iclrstrongname-strongnamekeydelete-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="80d0c-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="80d0c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80d0c-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="80d0c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="80d0c-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="80d0c-108">[in] Název kontejneru klíčů pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="80d0c-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="80d0c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="80d0c-109">Return Value</span></span>

<span data-ttu-id="80d0c-110">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="80d0c-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="80d0c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80d0c-111">Remarks</span></span>

<span data-ttu-id="80d0c-112">Použití [strongnamekeyinstall –](strongnamekeyinstall-function.md) k importu pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="80d0c-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="80d0c-113">Pokud `StrongNameKeyDelete` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="80d0c-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="80d0c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80d0c-114">Requirements</span></span>

<span data-ttu-id="80d0c-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d0c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="80d0c-116">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="80d0c-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="80d0c-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80d0c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="80d0c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d0c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="80d0c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80d0c-119">See also</span></span>

- [<span data-ttu-id="80d0c-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="80d0c-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="80d0c-121">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="80d0c-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="80d0c-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80d0c-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
