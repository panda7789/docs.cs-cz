---
title: ImportFileEx2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1c950e9a6e53e04cc0f2e52a140612562b32ff1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776978"
---
# <a name="importfileex2-method"></a><span data-ttu-id="c6cd4-102">ImportFileEx2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c6cd4-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="c6cd4-103">Importuje sestavení a nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="c6cd4-104">Tato metoda se podobá [metodě importFile –](importfile-method.md), ale funguje i v případě, že soubor, který importujete, na disku neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6cd4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6cd4-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6cd4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6cd4-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="c6cd4-107">Název souboru, který se má importovat</span><span class="sxs-lookup"><span data-stu-id="c6cd4-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="c6cd4-108">Volitelný název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="c6cd4-109">Volitelné rozhraní importu oboru rozhraní [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c6cd4-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="c6cd4-110">Při hodnotě TRUE se používá Importtypes –, jinak se import musí provést ručně.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="c6cd4-111">Příznaky, které mají být předány do [metody OpenScope –](../metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="c6cd4-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="c6cd4-112">Získá jedinečné ID pro sestavení nebo soubor.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="c6cd4-113">Přijímá import sestavení oboru [rozhraní IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c6cd4-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="c6cd4-114">Pokud soubor není sestavením, může mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="c6cd4-115">Přijímá počet importovaných souborů a oborů.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6cd4-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6cd4-116">Return Value</span></span>  
 <span data-ttu-id="c6cd4-117">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6cd4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6cd4-118">Requirements</span></span>  
 <span data-ttu-id="c6cd4-119">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c6cd4-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6cd4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6cd4-120">See also</span></span>

- [<span data-ttu-id="c6cd4-121">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6cd4-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c6cd4-122">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6cd4-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c6cd4-123">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c6cd4-123">ALink API</span></span>](index.md)
