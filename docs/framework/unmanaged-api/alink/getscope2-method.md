---
title: GetScope2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08c4a97b8cbc61a735bb9c1e6a31a698e7eefc1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787343"
---
# <a name="getscope2-method"></a><span data-ttu-id="77cb9-102">GetScope2 – metoda</span><span class="sxs-lookup"><span data-stu-id="77cb9-102">GetScope2 Method</span></span>
<span data-ttu-id="77cb9-103">Načte obor importu.</span><span class="sxs-lookup"><span data-stu-id="77cb9-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77cb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77cb9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="77cb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77cb9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="77cb9-106">ID cílového sestavení</span><span class="sxs-lookup"><span data-stu-id="77cb9-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="77cb9-107">ID souboru, ze kterého se má importovat</span><span class="sxs-lookup"><span data-stu-id="77cb9-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="77cb9-108">Rozsah založený na nule pro import.</span><span class="sxs-lookup"><span data-stu-id="77cb9-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="77cb9-109">Přijme ukazatel na rozhraní [rozhraní IMetaDataImport2](../metadata/imetadataimport2-interface.md) pro zadaný obor.</span><span class="sxs-lookup"><span data-stu-id="77cb9-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77cb9-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="77cb9-110">Return Value</span></span>  
 <span data-ttu-id="77cb9-111">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="77cb9-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77cb9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77cb9-112">Requirements</span></span>  
 <span data-ttu-id="77cb9-113">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="77cb9-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cb9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77cb9-114">See also</span></span>

- [<span data-ttu-id="77cb9-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77cb9-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="77cb9-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77cb9-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="77cb9-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="77cb9-117">ALink API</span></span>](index.md)
