---
title: StrongNameGetBlob – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095014"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="38393-102">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="38393-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="38393-103">Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="38393-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="38393-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="38393-104">This function has been deprecated.</span></span> <span data-ttu-id="38393-105">Místo toho použijte metodu [ICLRStrongName:: StrongNameGetBlob –](../hosting/iclrstrongname-strongnamegetblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="38393-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38393-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38393-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38393-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="38393-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="38393-108">pro Platná cesta ke spustitelnému souboru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="38393-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="38393-109">pro Vyrovnávací paměť, do které se má načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="38393-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="38393-110">[in, out] Požadovaná maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="38393-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="38393-111">Po návratu se skutečná velikost `pbBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="38393-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38393-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38393-112">Return Value</span></span>  
 <span data-ttu-id="38393-113">`true` po úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="38393-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38393-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38393-114">Remarks</span></span>  
 <span data-ttu-id="38393-115">Pokud se funkce `StrongNameGetBlob` nedokončila úspěšně, zavolejte funkci [StrongNameErrorInfo –](strongnameerrorinfo-function.md) , která načte poslední vygenerovanou chybu.</span><span class="sxs-lookup"><span data-stu-id="38393-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38393-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38393-116">Requirements</span></span>  
 <span data-ttu-id="38393-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38393-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38393-118">**Hlavička:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="38393-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="38393-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38393-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38393-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38393-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38393-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38393-121">See also</span></span>

- [<span data-ttu-id="38393-122">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="38393-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="38393-123">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="38393-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="38393-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38393-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
