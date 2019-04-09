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
ms.openlocfilehash: e438006d6424866514e73119c05e8fd69d7ba62e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132259"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="cb837-102">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="cb837-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="cb837-103">Vytvoří čtečku historie pro zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="cb837-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb837-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb837-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb837-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="cb837-106">[in] Cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="cb837-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="cb837-107">[out] Při úspěšném dokončení obsahuje ukazatel na historie čtečky.</span><span class="sxs-lookup"><span data-stu-id="cb837-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb837-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cb837-108">Return Value</span></span>  
 <span data-ttu-id="cb837-109">Tato metoda vrátí standardní kódy chyb modelu COM, jak je definovaný ve WinError.h, kromě hodnotami popsanými v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="cb837-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="cb837-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="cb837-110">Return code</span></span>|<span data-ttu-id="cb837-111">Popis</span><span class="sxs-lookup"><span data-stu-id="cb837-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cb837-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb837-112">S_OK</span></span>|<span data-ttu-id="cb837-113">Označuje, že metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="cb837-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="cb837-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cb837-114">E_INVALIDARG</span></span>|<span data-ttu-id="cb837-115">Označuje, že `wzFilePath` nebo `ppHistoryReader` jsou nastaveny na hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="cb837-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb837-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb837-116">Requirements</span></span>  
 <span data-ttu-id="cb837-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb837-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb837-118">**Knihovna:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="cb837-118">**Library:** Fusion.dll</span></span>  
  
 **<span data-ttu-id="cb837-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cb837-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb837-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb837-120">See also</span></span>

- [<span data-ttu-id="cb837-121">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="cb837-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
