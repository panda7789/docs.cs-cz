---
title: AddImport – metoda
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787662"
---
# <a name="addimport-method"></a><span data-ttu-id="854e7-102">AddImport – metoda</span><span class="sxs-lookup"><span data-stu-id="854e7-102">AddImport Method</span></span>
<span data-ttu-id="854e7-103">Přidá importy do sestavení.</span><span class="sxs-lookup"><span data-stu-id="854e7-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="854e7-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="854e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="854e7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="854e7-106">Jedinečné ID sestavení, které se má rozšířit</span><span class="sxs-lookup"><span data-stu-id="854e7-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="854e7-107">Jedinečné ID, které bylo načteno z [metody importFile –](importfile-method.md)souboru, který má být importován.</span><span class="sxs-lookup"><span data-stu-id="854e7-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="854e7-108">Značky `ffContainsNoMetaData` modelu COM+ FileDef jako a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="854e7-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="854e7-109">`dwFlags`je předán [metodě DefineFile –](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="854e7-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="854e7-110">Ukazatel na token, který obdrží ID pro výsledný soubor.</span><span class="sxs-lookup"><span data-stu-id="854e7-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="854e7-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="854e7-111">Return Value</span></span>  
 <span data-ttu-id="854e7-112">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="854e7-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854e7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="854e7-113">Requirements</span></span>  
 <span data-ttu-id="854e7-114">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="854e7-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854e7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="854e7-115">See also</span></span>

- [<span data-ttu-id="854e7-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="854e7-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="854e7-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="854e7-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="854e7-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="854e7-118">ALink API</span></span>](index.md)
