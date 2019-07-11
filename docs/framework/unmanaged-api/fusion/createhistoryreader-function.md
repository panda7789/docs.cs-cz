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
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778425"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="3ea62-102">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="3ea62-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="3ea62-103">Vytvoří čtečku historie pro zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="3ea62-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ea62-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ea62-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="3ea62-106">[in] Cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="3ea62-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="3ea62-107">[out] Při úspěšném dokončení obsahuje ukazatel na historie čtečky.</span><span class="sxs-lookup"><span data-stu-id="3ea62-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea62-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3ea62-108">Return Value</span></span>  
 <span data-ttu-id="3ea62-109">Tato metoda vrátí standardní kódy chyb modelu COM, jak je definovaný ve WinError.h, kromě hodnotami popsanými v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3ea62-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="3ea62-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="3ea62-110">Return code</span></span>|<span data-ttu-id="3ea62-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea62-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3ea62-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ea62-112">S_OK</span></span>|<span data-ttu-id="3ea62-113">Označuje, že metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="3ea62-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="3ea62-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3ea62-114">E_INVALIDARG</span></span>|<span data-ttu-id="3ea62-115">Označuje, že `wzFilePath` nebo `ppHistoryReader` jsou nastaveny na hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="3ea62-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ea62-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ea62-116">Requirements</span></span>  
 <span data-ttu-id="3ea62-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea62-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea62-118">**Knihovna:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="3ea62-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="3ea62-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea62-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea62-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ea62-120">See also</span></span>

- [<span data-ttu-id="3ea62-121">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="3ea62-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
