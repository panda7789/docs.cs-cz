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
ms.openlocfilehash: 9e441d4da64e9704fbda2368d2b07289aaea610a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125199"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="569ce-102">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="569ce-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="569ce-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="569ce-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="569ce-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="569ce-104">This function has been deprecated.</span></span> <span data-ttu-id="569ce-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameKeyInstall –](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .</span><span class="sxs-lookup"><span data-stu-id="569ce-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="569ce-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="569ce-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="569ce-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="569ce-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="569ce-108">pro Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="569ce-108">[in] The name of the key container.</span></span> <span data-ttu-id="569ce-109">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="569ce-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="569ce-110">pro Dvojice binárních klíčů.</span><span class="sxs-lookup"><span data-stu-id="569ce-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="569ce-111">pro Velikost `pbKeyBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="569ce-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="569ce-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="569ce-112">Return Value</span></span>

<span data-ttu-id="569ce-113">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="569ce-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="569ce-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="569ce-114">Remarks</span></span>

<span data-ttu-id="569ce-115">Pomocí funkce [StrongNameKeyDelete –](strongnamekeydelete-function.md) odstraňte kontejner klíčů.</span><span class="sxs-lookup"><span data-stu-id="569ce-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="569ce-116">Pokud se funkce `StrongNameKeyInstall` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="569ce-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="569ce-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="569ce-117">Requirements</span></span>

<span data-ttu-id="569ce-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="569ce-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="569ce-119">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="569ce-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="569ce-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="569ce-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="569ce-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="569ce-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="569ce-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="569ce-122">See also</span></span>

- [<span data-ttu-id="569ce-123">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="569ce-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="569ce-124">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="569ce-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="569ce-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="569ce-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
