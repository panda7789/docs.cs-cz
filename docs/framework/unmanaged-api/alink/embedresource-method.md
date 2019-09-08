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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f6140e5f85a7ee21773c96a5abdccadaddab92e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777456"
---
# <a name="embedresource-method"></a><span data-ttu-id="9d65a-102">EmbedResource – metoda</span><span class="sxs-lookup"><span data-stu-id="9d65a-102">EmbedResource Method</span></span>
<span data-ttu-id="9d65a-103">Deklaruje vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="9d65a-103">Declares an embedded resource.</span></span> <span data-ttu-id="9d65a-104">Tato metoda ve skutečnosti nevkládá prostředek.</span><span class="sxs-lookup"><span data-stu-id="9d65a-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d65a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d65a-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d65a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d65a-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9d65a-107">ID sestavení</span><span class="sxs-lookup"><span data-stu-id="9d65a-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9d65a-108">Token souboru nebo ID sestavení souboru, který obsahuje prostředek.</span><span class="sxs-lookup"><span data-stu-id="9d65a-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="9d65a-109">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="9d65a-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="9d65a-110">Posun prostředku od RVA.</span><span class="sxs-lookup"><span data-stu-id="9d65a-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d65a-111">Příznaky přístupnosti `mrPublic` , `mrPrivate`jako jsou a.</span><span class="sxs-lookup"><span data-stu-id="9d65a-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="9d65a-112">Tyto příznaky mohou být předány [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="9d65a-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d65a-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d65a-113">Return Value</span></span>  
 <span data-ttu-id="9d65a-114">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="9d65a-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d65a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d65a-115">Requirements</span></span>  
 <span data-ttu-id="9d65a-116">Vyžaduje ALink. h.</span><span class="sxs-lookup"><span data-stu-id="9d65a-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d65a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d65a-117">See also</span></span>

- [<span data-ttu-id="9d65a-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d65a-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9d65a-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d65a-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9d65a-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="9d65a-120">ALink API</span></span>](index.md)
