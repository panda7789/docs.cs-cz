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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aba11ccd61b65d2a779b39db8e0e082cf4d4015b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787214"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="18e70-102">SetAssemblyFile2 – metoda</span><span class="sxs-lookup"><span data-stu-id="18e70-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="18e70-103">Nastaví název a možnosti pro nové sestavení.</span><span class="sxs-lookup"><span data-stu-id="18e70-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="18e70-104">Nevolejte tuto metodu, když vytváříte nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="18e70-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e70-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18e70-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="18e70-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="18e70-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="18e70-107">Název souboru manifestu</span><span class="sxs-lookup"><span data-stu-id="18e70-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="18e70-108">Rozhraní [IMetaDataEmit2 rozhraní](../metadata/imetadataemit2-interface.md) pro tento soubor.</span><span class="sxs-lookup"><span data-stu-id="18e70-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="18e70-109">Možnosti reprezentované [výčtem AssemblyFlags –](../metadata/assemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="18e70-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="18e70-110">Získá jedinečné ID sestavení, které je sestaveno.</span><span class="sxs-lookup"><span data-stu-id="18e70-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18e70-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18e70-111">Return Value</span></span>  
 <span data-ttu-id="18e70-112">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="18e70-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18e70-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18e70-113">Requirements</span></span>  
 <span data-ttu-id="18e70-114">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="18e70-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e70-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18e70-115">See also</span></span>

- [<span data-ttu-id="18e70-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18e70-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="18e70-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18e70-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="18e70-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="18e70-118">ALink API</span></span>](index.md)
