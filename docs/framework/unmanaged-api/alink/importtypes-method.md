---
title: ImportTypes – metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445676"
---
# <a name="importtypes-method"></a><span data-ttu-id="da598-102">ImportTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="da598-102">ImportTypes Method</span></span>
<span data-ttu-id="da598-103">Inicializuje import typů z každého oboru importovaného pomocí [metody importFile –](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="da598-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da598-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da598-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="da598-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da598-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="da598-106">ID sestavení, do kterého se má importovat</span><span class="sxs-lookup"><span data-stu-id="da598-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="da598-107">ID souboru, ze kterého se má importovat</span><span class="sxs-lookup"><span data-stu-id="da598-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="da598-108">Rozsah založený na nule pro import.</span><span class="sxs-lookup"><span data-stu-id="da598-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="da598-109">Přijímá popisovač enumerátoru pro typy v tomto oboru.</span><span class="sxs-lookup"><span data-stu-id="da598-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="da598-110">Volitelně přijímá rozhraní [rozhraní IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="da598-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="da598-111">Volitelně přijímá počet typů v označeném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="da598-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da598-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da598-112">Return Value</span></span>  
 <span data-ttu-id="da598-113">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="da598-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da598-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da598-114">Requirements</span></span>  
 <span data-ttu-id="da598-115">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="da598-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da598-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da598-116">See also</span></span>

- [<span data-ttu-id="da598-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da598-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="da598-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da598-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="da598-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="da598-119">ALink API</span></span>](index.md)
