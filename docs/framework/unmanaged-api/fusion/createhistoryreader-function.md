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
ms.openlocfilehash: 2710d14d6e73879fd17a6b58659463ea205f2384
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795375"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="ba1a1-102">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="ba1a1-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="ba1a1-103">Vytvoří čtečku historie pro zadaný soubor.</span><span class="sxs-lookup"><span data-stu-id="ba1a1-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba1a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba1a1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba1a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba1a1-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="ba1a1-106">pro Cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="ba1a1-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="ba1a1-107">mimo Po úspěšném dokončení obsahuje ukazatel na čtečku historie.</span><span class="sxs-lookup"><span data-stu-id="ba1a1-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba1a1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ba1a1-108">Return Value</span></span>  
 <span data-ttu-id="ba1a1-109">Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v WinError. h, kromě hodnot popsaných v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ba1a1-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="ba1a1-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="ba1a1-110">Return code</span></span>|<span data-ttu-id="ba1a1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ba1a1-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ba1a1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba1a1-112">S_OK</span></span>|<span data-ttu-id="ba1a1-113">Označuje, že metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ba1a1-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="ba1a1-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ba1a1-114">E_INVALIDARG</span></span>|<span data-ttu-id="ba1a1-115">Označuje, `wzFilePath` že `ppHistoryReader` nebo jsou nastaveny na odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ba1a1-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba1a1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba1a1-116">Requirements</span></span>  
 <span data-ttu-id="ba1a1-117">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba1a1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba1a1-118">**Knihovna** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="ba1a1-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="ba1a1-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba1a1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1a1-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba1a1-120">See also</span></span>

- [<span data-ttu-id="ba1a1-121">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="ba1a1-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
