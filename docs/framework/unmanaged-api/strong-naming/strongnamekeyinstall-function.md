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
ms.openlocfilehash: 7121ace6777e7cf947fcc6ff30b1ea314851feff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636706"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="1ab6e-102">StrongNameKeyInstall – funkce</span><span class="sxs-lookup"><span data-stu-id="1ab6e-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="1ab6e-103">Importuje pár veřejného a privátního klíče do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="1ab6e-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-104">This function has been deprecated.</span></span> <span data-ttu-id="1ab6e-105">Použití [iclrstrongname::strongnamekeyinstall –](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ab6e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ab6e-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="1ab6e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ab6e-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="1ab6e-108">[in] Název kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-108">[in] The name of the key container.</span></span> <span data-ttu-id="1ab6e-109">`wszKeyContainer` musí být neprázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="1ab6e-110">[in] Binární pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="1ab6e-111">[in] Velikost v bajtech, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ab6e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ab6e-112">Return Value</span></span>

<span data-ttu-id="1ab6e-113">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ab6e-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ab6e-114">Remarks</span></span>

<span data-ttu-id="1ab6e-115">Použití [strongnamekeydelete –](strongnamekeydelete-function.md) funkce pro odstranění kontejneru klíčů.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="1ab6e-116">Pokud `StrongNameKeyInstall` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="1ab6e-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ab6e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ab6e-117">Requirements</span></span>

<span data-ttu-id="1ab6e-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ab6e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="1ab6e-119">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="1ab6e-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="1ab6e-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ab6e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="1ab6e-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ab6e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1ab6e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ab6e-122">See also</span></span>

- [<span data-ttu-id="1ab6e-123">StrongNameKeyInstall – metoda</span><span class="sxs-lookup"><span data-stu-id="1ab6e-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="1ab6e-124">StrongNameKeyDelete – metoda</span><span class="sxs-lookup"><span data-stu-id="1ab6e-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="1ab6e-125">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ab6e-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
