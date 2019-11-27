---
title: SetAssemblyFile2 – metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 4f710ef9741869a2b4fd8473ed3ecf379cfcc56d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445585"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="384ec-102">SetAssemblyFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="384ec-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="384ec-103">Nastaví název a možnosti pro nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="384ec-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="384ec-104">Nevolejte tuto metodu, když vytváříte nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="384ec-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384ec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="384ec-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="384ec-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="384ec-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="384ec-107">Název souboru manifestu</span><span class="sxs-lookup"><span data-stu-id="384ec-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="384ec-108">Rozhraní [IMetaDataEmit2 rozhraní](../metadata/imetadataemit2-interface.md) pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="384ec-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="384ec-109">Možnosti reprezentované [výčtem AssemblyFlags –](../metadata/assemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="384ec-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="384ec-110">Získá jedinečné ID sestavení, které je sestaveno.</span><span class="sxs-lookup"><span data-stu-id="384ec-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="384ec-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="384ec-111">Return Value</span></span>  
 <span data-ttu-id="384ec-112">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="384ec-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="384ec-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="384ec-113">Requirements</span></span>  
 <span data-ttu-id="384ec-114">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="384ec-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="384ec-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="384ec-115">See also</span></span>

- [<span data-ttu-id="384ec-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="384ec-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="384ec-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="384ec-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="384ec-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="384ec-118">ALink API</span></span>](index.md)
