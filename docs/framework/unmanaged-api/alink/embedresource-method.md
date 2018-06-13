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
ms.openlocfilehash: eb1fc266c8451953c8b6a9c686f4a1c1951966e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405395"
---
# <a name="embedresource-method"></a><span data-ttu-id="be675-102">EmbedResource – metoda</span><span class="sxs-lookup"><span data-stu-id="be675-102">EmbedResource Method</span></span>
<span data-ttu-id="be675-103">Deklaruje vložený prostředek.</span><span class="sxs-lookup"><span data-stu-id="be675-103">Declares an embedded resource.</span></span> <span data-ttu-id="be675-104">Tato metoda není ve skutečnosti vložit prostředek.</span><span class="sxs-lookup"><span data-stu-id="be675-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be675-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be675-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be675-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be675-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="be675-107">ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="be675-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="be675-108">Soubor ID souboru, který obsahuje prostředek token nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="be675-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="be675-109">Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="be675-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="be675-110">Posun prostředku z RVA.</span><span class="sxs-lookup"><span data-stu-id="be675-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="be675-111">Usnadnění flags – například `mrPublic` a `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="be675-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="be675-112">Může být předány tyto příznaky [defineexportedtype – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="be675-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be675-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="be675-113">Return Value</span></span>  
 <span data-ttu-id="be675-114">Vrátí S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="be675-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be675-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be675-115">Requirements</span></span>  
 <span data-ttu-id="be675-116">Vyžaduje alink.h.</span><span class="sxs-lookup"><span data-stu-id="be675-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be675-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="be675-117">See Also</span></span>  
 [<span data-ttu-id="be675-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be675-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="be675-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be675-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="be675-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="be675-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
