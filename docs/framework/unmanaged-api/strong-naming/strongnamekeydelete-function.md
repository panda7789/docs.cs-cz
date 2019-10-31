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
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141596"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="98e4e-102">StrongNameKeyDelete – funkce</span><span class="sxs-lookup"><span data-stu-id="98e4e-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="98e4e-103">Odstraní zadaný kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="98e4e-103">Deletes the specified key container.</span></span>

<span data-ttu-id="98e4e-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="98e4e-104">This function has been deprecated.</span></span> <span data-ttu-id="98e4e-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyDelete –](../hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98e4e-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="98e4e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98e4e-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="98e4e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="98e4e-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="98e4e-108">pro Název kontejneru klíčů, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="98e4e-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="98e4e-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="98e4e-109">Return Value</span></span>

<span data-ttu-id="98e4e-110">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="98e4e-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="98e4e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98e4e-111">Remarks</span></span>

<span data-ttu-id="98e4e-112">Pomocí funkce [StrongNameKeyInstall –](strongnamekeyinstall-function.md) importujte pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="98e4e-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="98e4e-113">Pokud se funkce `StrongNameKeyDelete` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="98e4e-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="98e4e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98e4e-114">Requirements</span></span>

<span data-ttu-id="98e4e-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e4e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="98e4e-116">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="98e4e-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="98e4e-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="98e4e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="98e4e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e4e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="98e4e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98e4e-119">See also</span></span>

- [<span data-ttu-id="98e4e-120">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="98e4e-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="98e4e-121">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="98e4e-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="98e4e-122">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98e4e-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
