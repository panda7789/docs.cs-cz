---
title: ImportTypes2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787253"
---
# <a name="importtypes2-method"></a><span data-ttu-id="cff45-102">ImportTypes2 – metoda</span><span class="sxs-lookup"><span data-stu-id="cff45-102">ImportTypes2 Method</span></span>
<span data-ttu-id="cff45-103">Inicializuje import typů.</span><span class="sxs-lookup"><span data-stu-id="cff45-103">Initiates the import of types.</span></span> <span data-ttu-id="cff45-104">Zavolejte tuto metodu pro zahájení importu typů z každého oboru importovaného prostřednictvím [metody importFile –](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="cff45-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff45-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cff45-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="cff45-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cff45-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="cff45-107">ID sestavení, do kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="cff45-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="cff45-108">ID souboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="cff45-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="cff45-109">Rozsah od nuly, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="cff45-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="cff45-110">Přijímá popisovač enumerátoru pro typy v daném oboru.</span><span class="sxs-lookup"><span data-stu-id="cff45-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="cff45-111">Volitelně přijímá rozhraní [rozhraní IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cff45-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="cff45-112">Volitelně přijímá počet typů v zadaném oboru.</span><span class="sxs-lookup"><span data-stu-id="cff45-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cff45-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cff45-113">Return Value</span></span>  
 <span data-ttu-id="cff45-114">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="cff45-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff45-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cff45-115">Requirements</span></span>  
 <span data-ttu-id="cff45-116">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="cff45-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff45-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cff45-117">See also</span></span>

- [<span data-ttu-id="cff45-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cff45-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="cff45-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cff45-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="cff45-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="cff45-120">ALink API</span></span>](index.md)
