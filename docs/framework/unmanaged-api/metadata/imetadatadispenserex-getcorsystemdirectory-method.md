---
title: IMetaDataDispenserEx::GetCORSystemDirectory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: a76c17e663fdf6555ed878cca1b86b6a9395730e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008791"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="72224-102">IMetaDataDispenserEx::GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="72224-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="72224-103">Načte adresář, který obsahuje aktuální modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="72224-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="72224-104">Tato metoda je podporována pouze pro použití vnitroprocesové ladicí program.</span><span class="sxs-lookup"><span data-stu-id="72224-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="72224-105">Pokud se volá z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="72224-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72224-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72224-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72224-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="72224-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="72224-108">mimo Vyrovnávací paměť pro získání názvu adresáře.</span><span class="sxs-lookup"><span data-stu-id="72224-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="72224-109">pro Velikost v bajtech `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="72224-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="72224-110">mimo Počet bajtů, které se ve skutečnosti vrátily `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="72224-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72224-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72224-111">Requirements</span></span>  
 <span data-ttu-id="72224-112">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72224-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72224-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="72224-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72224-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="72224-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72224-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72224-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72224-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="72224-116">See also</span></span>

- [<span data-ttu-id="72224-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72224-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="72224-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72224-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
