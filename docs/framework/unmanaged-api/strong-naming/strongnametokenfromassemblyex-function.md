---
title: StrongNameTokenFromAssemblyEx – funkce
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104238"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="f167d-102">StrongNameTokenFromAssemblyEx – funkce</span><span class="sxs-lookup"><span data-stu-id="f167d-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="f167d-103">Vytvoří token silného názvu ze zadaného souboru sestavení a vrátí veřejný klíč, který token představuje.</span><span class="sxs-lookup"><span data-stu-id="f167d-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="f167d-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f167d-104">This function has been deprecated.</span></span> <span data-ttu-id="f167d-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameTokenFromAssemblyEx –](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f167d-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f167d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f167d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f167d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f167d-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f167d-108">pro Cesta k přenosnému spustitelnému souboru (PE) pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="f167d-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f167d-109">mimo Vrácený token silného názvu.</span><span class="sxs-lookup"><span data-stu-id="f167d-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f167d-110">mimo Velikost tokenu silného názvu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f167d-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f167d-111">mimo Vrácený veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="f167d-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f167d-112">mimo Velikost veřejného klíče v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f167d-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f167d-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f167d-113">Return Value</span></span>  
 <span data-ttu-id="f167d-114">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="f167d-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f167d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f167d-115">Remarks</span></span>  
 <span data-ttu-id="f167d-116">Token silného názvu je zkrácenou formou veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="f167d-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="f167d-117">Token je 64 hodnota hash, která je vytvořena z veřejného klíče použitého k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="f167d-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="f167d-118">Token je součástí silného názvu sestavení a lze ho číst z metadat sestavení.</span><span class="sxs-lookup"><span data-stu-id="f167d-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="f167d-119">Po načtení klíče a vytvoření tokenu byste měli zavolat funkci [StrongNameFreeBuffer –](strongnamefreebuffer-function.md) a uvolnit tak přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="f167d-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f167d-120">Pokud se funkce `StrongNameTokenFromAssemblyEx` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="f167d-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f167d-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f167d-121">Requirements</span></span>  
 <span data-ttu-id="f167d-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f167d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f167d-123">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f167d-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f167d-124">**Knihovna:** Zahrnuto jako prostředek v knihovně Mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f167d-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f167d-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f167d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f167d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f167d-126">See also</span></span>

- [<span data-ttu-id="f167d-127">StrongNameTokenFromAssemblyEx – metoda</span><span class="sxs-lookup"><span data-stu-id="f167d-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="f167d-128">StrongNameTokenFromAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="f167d-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="f167d-129">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f167d-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
