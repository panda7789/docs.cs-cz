---
title: SetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 180eb1a3129cfcd96668ecfee11947c15c5e0915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776909"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="21010-102">SetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="21010-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="21010-103">Přiřadí vlastnosti na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="21010-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21010-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21010-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="21010-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21010-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="21010-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="21010-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="21010-107">Soubor, který definuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="21010-107">File that defines the property.</span></span> <span data-ttu-id="21010-108">Může mít hodnotu null `AssemblyID` , pokud neoznačuje nevázaný netmodule.</span><span class="sxs-lookup"><span data-stu-id="21010-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="21010-109">Určuje možnost, kterou chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="21010-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="21010-110">Nová hodnota možnosti</span><span class="sxs-lookup"><span data-stu-id="21010-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21010-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21010-111">Return Value</span></span>  
 <span data-ttu-id="21010-112">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="21010-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21010-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21010-113">Requirements</span></span>  
 <span data-ttu-id="21010-114">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="21010-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21010-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21010-115">See also</span></span>

- [<span data-ttu-id="21010-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21010-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="21010-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21010-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="21010-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="21010-118">ALink API</span></span>](index.md)
