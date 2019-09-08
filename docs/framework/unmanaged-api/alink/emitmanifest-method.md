---
title: EmitManifest – metoda
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdab1fd10be8fd245f4348798232964721b4487a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777338"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="f1d76-102">EmitManifest – metoda</span><span class="sxs-lookup"><span data-stu-id="f1d76-102">EmitManifest Method</span></span>
<span data-ttu-id="f1d76-103">Vygeneruje finální manifest.</span><span class="sxs-lookup"><span data-stu-id="f1d76-103">Emits the final manifest.</span></span> <span data-ttu-id="f1d76-104">Po importu všech ostatních souborů a nastavení všech možností volejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="f1d76-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="f1d76-105">Nevolejte tuto metodu pro nevázané moduly.</span><span class="sxs-lookup"><span data-stu-id="f1d76-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1d76-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1d76-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1d76-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1d76-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f1d76-108">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="f1d76-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="f1d76-109">Přijme velikost, která se má rezervovat v souboru sestavení, načtená z [funkce StrongNameSignatureSize –](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="f1d76-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="f1d76-110">Volitelně obdrží token manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f1d76-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1d76-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f1d76-111">Return Value</span></span>  
 <span data-ttu-id="f1d76-112">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f1d76-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1d76-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1d76-113">Requirements</span></span>  
 <span data-ttu-id="f1d76-114">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="f1d76-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1d76-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1d76-115">See also</span></span>

- [<span data-ttu-id="f1d76-116">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1d76-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f1d76-117">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1d76-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f1d76-118">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="f1d76-118">ALink API</span></span>](index.md)
