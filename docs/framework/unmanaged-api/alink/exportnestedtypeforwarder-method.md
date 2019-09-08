---
title: ExportNestedTypeForwarder – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb8112d6d2b5c2cbb257db2f20ff4be5a84e827b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787463"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="99dd2-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="99dd2-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="99dd2-103">Přidá předávaného typu pro vnořený typ do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="99dd2-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99dd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99dd2-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="99dd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99dd2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="99dd2-106">ID sestavení, ze kterého se má exportovat</span><span class="sxs-lookup"><span data-stu-id="99dd2-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="99dd2-107">Token souboru nebo ID sestavení souboru, který definuje typ.</span><span class="sxs-lookup"><span data-stu-id="99dd2-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="99dd2-108">Token pro typ</span><span class="sxs-lookup"><span data-stu-id="99dd2-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="99dd2-109">Token nadřazeného typu</span><span class="sxs-lookup"><span data-stu-id="99dd2-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="99dd2-110">Plně kvalifikovaný název typu, který se má exportovat</span><span class="sxs-lookup"><span data-stu-id="99dd2-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="99dd2-111">`ComType`příznaky jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="99dd2-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="99dd2-112">Přijímá token pro typ exportu.</span><span class="sxs-lookup"><span data-stu-id="99dd2-112">Receives token of export type.</span></span> <span data-ttu-id="99dd2-113">To je nezbytné jenom pro vygenerování vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="99dd2-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99dd2-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99dd2-114">Return Value</span></span>  
 <span data-ttu-id="99dd2-115">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="99dd2-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99dd2-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99dd2-116">Requirements</span></span>  
 <span data-ttu-id="99dd2-117">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="99dd2-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99dd2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99dd2-118">See also</span></span>

- [<span data-ttu-id="99dd2-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99dd2-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="99dd2-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99dd2-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="99dd2-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="99dd2-121">ALink API</span></span>](index.md)
