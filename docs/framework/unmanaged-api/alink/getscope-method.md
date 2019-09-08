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
ms.openlocfilehash: b3a0e42e9ffb99896bdd09dbbab65eafb40cafff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777205"
---
# <a name="getscope-method"></a><span data-ttu-id="bc18d-102">GetScope – metoda</span><span class="sxs-lookup"><span data-stu-id="bc18d-102">GetScope Method</span></span>
<span data-ttu-id="bc18d-103">Načte obor importu.</span><span class="sxs-lookup"><span data-stu-id="bc18d-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc18d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc18d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc18d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc18d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bc18d-106">Jedinečné ID sestavení, do kterého se má importovat</span><span class="sxs-lookup"><span data-stu-id="bc18d-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="bc18d-107">Jedinečné ID souboru, ze kterého se má importovat</span><span class="sxs-lookup"><span data-stu-id="bc18d-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="bc18d-108">Rozsah založený na nule pro import.</span><span class="sxs-lookup"><span data-stu-id="bc18d-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="bc18d-109">Přijímá rozhraní [rozhraní IMetaDataImport](../metadata/imetadataimport-interface.md) pro daný obor.</span><span class="sxs-lookup"><span data-stu-id="bc18d-109">Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc18d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bc18d-110">Return Value</span></span>  
 <span data-ttu-id="bc18d-111">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="bc18d-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc18d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc18d-112">Requirements</span></span>  
 <span data-ttu-id="bc18d-113">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="bc18d-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc18d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc18d-114">See also</span></span>

- [<span data-ttu-id="bc18d-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc18d-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="bc18d-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc18d-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="bc18d-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="bc18d-117">ALink API</span></span>](index.md)
