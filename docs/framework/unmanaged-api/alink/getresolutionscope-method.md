---
title: GetResolutionScope – metoda
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: f2b78b35db6306c82e389955c4824875bcf25334
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447222"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="c7f70-102">GetResolutionScope – metoda</span><span class="sxs-lookup"><span data-stu-id="c7f70-102">GetResolutionScope Method</span></span>
<span data-ttu-id="c7f70-103">Načte rozsah daného typu.</span><span class="sxs-lookup"><span data-stu-id="c7f70-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7f70-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7f70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7f70-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c7f70-106">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="c7f70-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c7f70-107">Soubor, který je nutný pro odkaz.</span><span class="sxs-lookup"><span data-stu-id="c7f70-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="c7f70-108">Token souboru, ve kterém je definován typ, obvykle načten pomocí [metody importFile –](importfile-method.md)</span><span class="sxs-lookup"><span data-stu-id="c7f70-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="c7f70-109">Přijme odkaz na sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="c7f70-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7f70-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c7f70-110">Return Value</span></span>  
 <span data-ttu-id="c7f70-111">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="c7f70-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7f70-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7f70-112">Requirements</span></span>  
 <span data-ttu-id="c7f70-113">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c7f70-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f70-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7f70-114">See also</span></span>

- [<span data-ttu-id="c7f70-115">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7f70-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c7f70-116">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7f70-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c7f70-117">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="c7f70-117">ALink API</span></span>](index.md)
