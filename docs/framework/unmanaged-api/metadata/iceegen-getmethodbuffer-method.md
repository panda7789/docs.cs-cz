---
title: ICeeGen::GetMethodBuffer – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
ms.openlocfilehash: 99eef11c294dbb17b30b2ef28e65999d4d60f817
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008315"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="36ce7-102">ICeeGen::GetMethodBuffer – metoda</span><span class="sxs-lookup"><span data-stu-id="36ce7-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="36ce7-103">Načte vyrovnávací paměť odpovídající velikosti pro metodu na zadané relativní virtuální adrese.</span><span class="sxs-lookup"><span data-stu-id="36ce7-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="36ce7-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="36ce7-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ce7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36ce7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36ce7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="36ce7-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="36ce7-107">pro Relativní virtuální adresa metody, pro kterou se má vrátit vyrovnávací paměť</span><span class="sxs-lookup"><span data-stu-id="36ce7-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="36ce7-108">mimo Ukazatel na vrácenou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="36ce7-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36ce7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36ce7-109">Requirements</span></span>  
 <span data-ttu-id="36ce7-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36ce7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36ce7-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="36ce7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36ce7-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="36ce7-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36ce7-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36ce7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ce7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="36ce7-114">See also</span></span>

- [<span data-ttu-id="36ce7-115">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36ce7-115">ICeeGen Interface</span></span>](iceegen-interface.md)
