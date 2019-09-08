---
title: AddFile2 – metoda
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3a6892dbed172c0be3b036014d393657dbc8593
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777517"
---
# <a name="addfile2-method"></a><span data-ttu-id="40241-102">AddFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="40241-102">AddFile2 Method</span></span>
<span data-ttu-id="40241-103">Přidá soubory do sestavení.</span><span class="sxs-lookup"><span data-stu-id="40241-103">Adds files to the assembly.</span></span> <span data-ttu-id="40241-104">Lze také použít k vytvoření nevázaných modulů.</span><span class="sxs-lookup"><span data-stu-id="40241-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40241-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40241-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="40241-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="40241-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="40241-107">ID pro sestavení, ke kterému je soubor přidán.</span><span class="sxs-lookup"><span data-stu-id="40241-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="40241-108">Název souboru, který se má přidat</span><span class="sxs-lookup"><span data-stu-id="40241-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="40241-109">Příznaky `FileDef` modelu COM+, `ffContainsNoMetaData` například `ffWriteable`a.</span><span class="sxs-lookup"><span data-stu-id="40241-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="40241-110">`dwFlags`je předán [metodě DefineFile –](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="40241-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="40241-111">Rozhraní k rozhraní [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="40241-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="40241-112">Získá ID přidávaného souboru.</span><span class="sxs-lookup"><span data-stu-id="40241-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40241-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40241-113">Return Value</span></span>  
 <span data-ttu-id="40241-114">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="40241-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40241-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40241-115">Requirements</span></span>  
 <span data-ttu-id="40241-116">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="40241-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40241-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40241-117">See also</span></span>

- [<span data-ttu-id="40241-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40241-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="40241-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40241-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="40241-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="40241-120">ALink API</span></span>](index.md)
