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
ms.openlocfilehash: cc81ccd1c754e3d34c54737f4560b4f81d5cc916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438411"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="8b1a4-102">ExportNestedTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="8b1a4-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="8b1a4-103">Přidá předávaného typu pro vnořený typ do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b1a4-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b1a4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8b1a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b1a4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8b1a4-106">ID sestavení, ze kterého se má exportovat</span><span class="sxs-lookup"><span data-stu-id="8b1a4-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8b1a4-107">Token souboru nebo ID sestavení souboru, který definuje typ.</span><span class="sxs-lookup"><span data-stu-id="8b1a4-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="8b1a4-108">Token pro typ</span><span class="sxs-lookup"><span data-stu-id="8b1a4-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="8b1a4-109">Token nadřazeného typu</span><span class="sxs-lookup"><span data-stu-id="8b1a4-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="8b1a4-110">Plně kvalifikovaný název typu, který se má exportovat</span><span class="sxs-lookup"><span data-stu-id="8b1a4-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8b1a4-111">`ComType` příznaky jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="8b1a4-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="8b1a4-112">Přijímá token pro typ exportu.</span><span class="sxs-lookup"><span data-stu-id="8b1a4-112">Receives token of export type.</span></span> <span data-ttu-id="8b1a4-113">To je nezbytné jenom pro vygenerování vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="8b1a4-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b1a4-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8b1a4-114">Return Value</span></span>  
 <span data-ttu-id="8b1a4-115">Vrátí S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8b1a4-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b1a4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b1a4-116">Requirements</span></span>  
 <span data-ttu-id="8b1a4-117">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="8b1a4-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1a4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b1a4-118">See also</span></span>

- [<span data-ttu-id="8b1a4-119">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b1a4-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8b1a4-120">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b1a4-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8b1a4-121">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8b1a4-121">ALink API</span></span>](index.md)
