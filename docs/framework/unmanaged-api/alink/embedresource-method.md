---
title: EmbedResource – metoda
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 24279870e7406de649df56e8aad31252513e95c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446533"
---
# <a name="embedresource-method"></a><span data-ttu-id="eab7f-102">EmbedResource – metoda</span><span class="sxs-lookup"><span data-stu-id="eab7f-102">EmbedResource Method</span></span>
<span data-ttu-id="eab7f-103">Deklaruje vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="eab7f-103">Declares an embedded resource.</span></span> <span data-ttu-id="eab7f-104">Tato metoda ve skutečnosti nevkládá prostředek.</span><span class="sxs-lookup"><span data-stu-id="eab7f-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab7f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eab7f-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="eab7f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eab7f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eab7f-107">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="eab7f-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="eab7f-108">Token souboru nebo ID sestavení souboru, který obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="eab7f-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="eab7f-109">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="eab7f-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="eab7f-110">Posun prostředku od RVA.</span><span class="sxs-lookup"><span data-stu-id="eab7f-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eab7f-111">Příznaky přístupnosti, například `mrPublic` a `mrPrivate`</span><span class="sxs-lookup"><span data-stu-id="eab7f-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="eab7f-112">Tyto příznaky mohou být předány [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="eab7f-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eab7f-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eab7f-113">Return Value</span></span>  
 <span data-ttu-id="eab7f-114">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="eab7f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab7f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eab7f-115">Requirements</span></span>  
 <span data-ttu-id="eab7f-116">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="eab7f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab7f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eab7f-117">See also</span></span>

- [<span data-ttu-id="eab7f-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab7f-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="eab7f-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab7f-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="eab7f-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="eab7f-120">ALink API</span></span>](index.md)
