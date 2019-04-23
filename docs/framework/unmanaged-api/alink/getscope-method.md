---
title: GetScope – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 571612796d4e66be9dd8469d748c2380c839ddfa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165777"
---
# <a name="getscope-method"></a><span data-ttu-id="ea34a-102">GetScope – metoda</span><span class="sxs-lookup"><span data-stu-id="ea34a-102">GetScope Method</span></span>
<span data-ttu-id="ea34a-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="ea34a-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea34a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea34a-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea34a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea34a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ea34a-106">Jedinečné ID sestavení, které chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="ea34a-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ea34a-107">Jedinečné ID souboru pro import z.</span><span class="sxs-lookup"><span data-stu-id="ea34a-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="ea34a-108">Založený na nule oboru k importu.</span><span class="sxs-lookup"><span data-stu-id="ea34a-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="ea34a-109">Přijímá [imetadataimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní pro obor.</span><span class="sxs-lookup"><span data-stu-id="ea34a-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea34a-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ea34a-110">Return Value</span></span>  
 <span data-ttu-id="ea34a-111">Pokud metoda uspěje, vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="ea34a-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea34a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea34a-112">Requirements</span></span>  
 <span data-ttu-id="ea34a-113">Vyžaduje alink.h</span><span class="sxs-lookup"><span data-stu-id="ea34a-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea34a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea34a-114">See also</span></span>

- [<span data-ttu-id="ea34a-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea34a-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ea34a-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea34a-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ea34a-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ea34a-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
