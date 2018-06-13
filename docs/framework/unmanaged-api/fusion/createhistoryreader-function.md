---
title: CreateHistoryReader – funkce
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3a3cc21dbbcfa99ddcecb534bd2e337da005597
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431175"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="ad7df-102">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="ad7df-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="ad7df-103">Vytvoří historie čtečky zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="ad7df-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad7df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad7df-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad7df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad7df-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="ad7df-106">[v] Cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="ad7df-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="ad7df-107">[out] Při úspěšném dokončení obsahuje ukazatel na historie čtečky.</span><span class="sxs-lookup"><span data-stu-id="ad7df-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad7df-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad7df-108">Return Value</span></span>  
 <span data-ttu-id="ad7df-109">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h, kromě hodnot, které jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ad7df-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="ad7df-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="ad7df-110">Return code</span></span>|<span data-ttu-id="ad7df-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ad7df-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ad7df-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad7df-112">S_OK</span></span>|<span data-ttu-id="ad7df-113">Označuje, že metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ad7df-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="ad7df-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad7df-114">E_INVALIDARG</span></span>|<span data-ttu-id="ad7df-115">Určuje, že `wzFilePath` nebo `ppHistoryReader` jsou nastaveny na hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="ad7df-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad7df-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad7df-116">Requirements</span></span>  
 <span data-ttu-id="ad7df-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad7df-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad7df-118">**Knihovna:** knihovna Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="ad7df-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="ad7df-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad7df-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7df-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad7df-120">See Also</span></span>  
 [<span data-ttu-id="ad7df-121">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="ad7df-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
