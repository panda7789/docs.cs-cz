---
title: AddFile – metoda
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 4dd104805d547613315335bc9c95b5c60a9cab14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446680"
---
# <a name="addfile-method"></a><span data-ttu-id="6bc70-102">AddFile – metoda</span><span class="sxs-lookup"><span data-stu-id="6bc70-102">AddFile Method</span></span>
<span data-ttu-id="6bc70-103">Přidá soubory do sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bc70-103">Adds files to the assembly.</span></span> <span data-ttu-id="6bc70-104">Lze také použít k vytvoření nevázaných modulů.</span><span class="sxs-lookup"><span data-stu-id="6bc70-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc70-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bc70-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bc70-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bc70-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6bc70-107">Jedinečné ID sestavení, které se má rozšířit</span><span class="sxs-lookup"><span data-stu-id="6bc70-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="6bc70-108">Plně kvalifikovaný název souboru, který se má přidat</span><span class="sxs-lookup"><span data-stu-id="6bc70-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6bc70-109">Značky COM+ FileDef, například `ffContainsNoMetaData` a `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="6bc70-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="6bc70-110">`dwFlags` se předává do [metody DefineFile –](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="6bc70-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="6bc70-111">Rozhraní [rozhraní IMetaDataEmit](../metadata/imetadataemit-interface.md) , které se v případě potřeby používá k vygenerování metadat.</span><span class="sxs-lookup"><span data-stu-id="6bc70-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="6bc70-112">Ukazatel na místo, kde bude uloženo jedinečné ID přidaného souboru.</span><span class="sxs-lookup"><span data-stu-id="6bc70-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bc70-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bc70-113">Return Value</span></span>  
 <span data-ttu-id="6bc70-114">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6bc70-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bc70-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bc70-115">Requirements</span></span>  
 <span data-ttu-id="6bc70-116">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="6bc70-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc70-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bc70-117">See also</span></span>

- [<span data-ttu-id="6bc70-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bc70-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6bc70-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bc70-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6bc70-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="6bc70-120">ALink API</span></span>](index.md)
