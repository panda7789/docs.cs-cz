---
title: StrongNameKeyInstall – funkce
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798991"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="bcd0f-102">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="bcd0f-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="bcd0f-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="bcd0f-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-104">This function has been deprecated.</span></span> <span data-ttu-id="bcd0f-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyInstall –](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bcd0f-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="bcd0f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcd0f-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="bcd0f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcd0f-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="bcd0f-108">pro Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-108">[in] The name of the key container.</span></span> <span data-ttu-id="bcd0f-109">`wszKeyContainer`musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="bcd0f-110">pro Dvojice binárních klíčů.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="bcd0f-111">pro Velikost v bajtech `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="bcd0f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bcd0f-112">Return Value</span></span>

<span data-ttu-id="bcd0f-113">`true`Po úspěšném dokončení; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="bcd0f-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="bcd0f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcd0f-114">Remarks</span></span>

<span data-ttu-id="bcd0f-115">Pomocí funkce [StrongNameKeyDelete –](strongnamekeydelete-function.md) odstraňte kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="bcd0f-116">Pokud se `StrongNameKeyInstall` funkce nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="bcd0f-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="bcd0f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcd0f-117">Requirements</span></span>

<span data-ttu-id="bcd0f-118">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcd0f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="bcd0f-119">**Hlaviček** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bcd0f-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="bcd0f-120">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bcd0f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="bcd0f-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcd0f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bcd0f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcd0f-122">See also</span></span>

- [<span data-ttu-id="bcd0f-123">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="bcd0f-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="bcd0f-124">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="bcd0f-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="bcd0f-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcd0f-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
