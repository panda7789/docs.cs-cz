---
title: ExportType – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 455f71c5b576d1b57db591dab2a3e59f8a5eed67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777282"
---
# <a name="exporttype-method"></a><span data-ttu-id="8becd-102">ExportType – metoda</span><span class="sxs-lookup"><span data-stu-id="8becd-102">ExportType Method</span></span>
<span data-ttu-id="8becd-103">Určuje, že je možné exportovat typ.</span><span class="sxs-lookup"><span data-stu-id="8becd-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8becd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8becd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8becd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8becd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8becd-106">ID sestavení, ze kterého se má exportovat</span><span class="sxs-lookup"><span data-stu-id="8becd-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8becd-107">Token souboru nebo ID sestavení souboru, který definuje exportovatelný typ.</span><span class="sxs-lookup"><span data-stu-id="8becd-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="8becd-108">Token typu, který se má provést export.</span><span class="sxs-lookup"><span data-stu-id="8becd-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="8becd-109">Plně kvalifikovaný název typu, který se dá exportovat.</span><span class="sxs-lookup"><span data-stu-id="8becd-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8becd-110">`ComType`příznaky jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="8becd-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="8becd-111">Tento parametr může být předán [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="8becd-111">This parameter may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="8becd-112">Přijímá token pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="8becd-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8becd-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8becd-113">Return Value</span></span>  
 <span data-ttu-id="8becd-114">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="8becd-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8becd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8becd-115">Requirements</span></span>  
 <span data-ttu-id="8becd-116">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="8becd-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8becd-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8becd-117">See also</span></span>

- [<span data-ttu-id="8becd-118">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8becd-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8becd-119">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8becd-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8becd-120">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="8becd-120">ALink API</span></span>](index.md)
