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
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179400"
---
# <a name="getscope2-method"></a><span data-ttu-id="565d3-102">GetScope2 – metoda</span><span class="sxs-lookup"><span data-stu-id="565d3-102">GetScope2 Method</span></span>
<span data-ttu-id="565d3-103">Získá obor importu.</span><span class="sxs-lookup"><span data-stu-id="565d3-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="565d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="565d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="565d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="565d3-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="565d3-106">ID cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="565d3-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="565d3-107">ID souboru, ze kterého chcete importovat.</span><span class="sxs-lookup"><span data-stu-id="565d3-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="565d3-108">Obor založený na nule k importu.</span><span class="sxs-lookup"><span data-stu-id="565d3-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="565d3-109">Přijímá ukazatel na rozhraní [rozhraní IMetaDataImport2](../metadata/imetadataimport2-interface.md) pro uvedený obor.</span><span class="sxs-lookup"><span data-stu-id="565d3-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="565d3-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="565d3-110">Return Value</span></span>  
 <span data-ttu-id="565d3-111">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="565d3-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="565d3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="565d3-112">Requirements</span></span>  
 <span data-ttu-id="565d3-113">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="565d3-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565d3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="565d3-114">See also</span></span>

- [<span data-ttu-id="565d3-115">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="565d3-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="565d3-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="565d3-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="565d3-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="565d3-117">ALink API</span></span>](index.md)
