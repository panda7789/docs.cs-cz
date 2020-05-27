---
title: ICeeGen::GetSectionDataLen – metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 1855c73849c35bf709b0af261a88e6cd7a40abfb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008297"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="ec037-102">ICeeGen::GetSectionDataLen – metoda</span><span class="sxs-lookup"><span data-stu-id="ec037-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="ec037-103">Získá délku zadaného oddílu.</span><span class="sxs-lookup"><span data-stu-id="ec037-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="ec037-104">Tato metoda je zastaralá a neměla by se používat.</span><span class="sxs-lookup"><span data-stu-id="ec037-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec037-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec037-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec037-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec037-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ec037-107">pro Datová část, jejíž délka bude načtena.</span><span class="sxs-lookup"><span data-stu-id="ec037-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="ec037-108">mimo Vrácená délka zadaného oddílu.</span><span class="sxs-lookup"><span data-stu-id="ec037-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec037-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec037-109">Remarks</span></span>  
 <span data-ttu-id="ec037-110">Volejte `GetSectionDataLen` pouze v případě, že máte zvláštní požadavky na oddíly, které nejsou zpracovány jinými metodami.</span><span class="sxs-lookup"><span data-stu-id="ec037-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec037-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec037-111">Requirements</span></span>  
 <span data-ttu-id="ec037-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec037-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec037-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec037-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec037-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="ec037-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec037-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec037-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec037-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec037-116">See also</span></span>

- [<span data-ttu-id="ec037-117">ICeeGen – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ec037-117">ICeeGen Interface</span></span>](iceegen-interface.md)
