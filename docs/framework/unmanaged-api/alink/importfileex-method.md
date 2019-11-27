---
title: ImportFileEx – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
ms.openlocfilehash: bee7db61beb9ed8c00cf584924be690a67d92eac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446948"
---
# <a name="importfileex-method"></a><span data-ttu-id="0e10c-102">ImportFileEx – metoda</span><span class="sxs-lookup"><span data-stu-id="0e10c-102">ImportFileEx Method</span></span>
<span data-ttu-id="0e10c-103">Importuje označené sestavení nebo nevázaný modul.</span><span class="sxs-lookup"><span data-stu-id="0e10c-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e10c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e10c-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e10c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e10c-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0e10c-106">Plně kvalifikovaný název souboru, ze kterého se má importovat.</span><span class="sxs-lookup"><span data-stu-id="0e10c-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="0e10c-107">Volitelný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="0e10c-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="0e10c-108">Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.</span><span class="sxs-lookup"><span data-stu-id="0e10c-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="0e10c-109">Příznaky, které mají být předány do [metody OpenScope –](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="0e10c-109">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="0e10c-110">Získá ID importovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0e10c-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="0e10c-111">Přijímá import sestavení oboru [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0e10c-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="0e10c-112">Je nastaven na hodnotu NULL, pokud soubor není sestavení.</span><span class="sxs-lookup"><span data-stu-id="0e10c-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="0e10c-113">Přijímá počet importovaných souborů a rozsahů.</span><span class="sxs-lookup"><span data-stu-id="0e10c-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e10c-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0e10c-114">Return Value</span></span>  
 <span data-ttu-id="0e10c-115">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="0e10c-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e10c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e10c-116">Requirements</span></span>  
 <span data-ttu-id="0e10c-117">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="0e10c-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e10c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e10c-118">See also</span></span>

- [<span data-ttu-id="0e10c-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e10c-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="0e10c-120">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e10c-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="0e10c-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="0e10c-121">ALink API</span></span>](index.md)
