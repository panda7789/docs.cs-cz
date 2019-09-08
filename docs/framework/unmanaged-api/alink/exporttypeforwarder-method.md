---
title: ExportTypeForwarder – metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae4ddd07a2a3d3ab9b5d024eceb43329db96915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787506"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="ac0fb-102">ExportTypeForwarder – metoda</span><span class="sxs-lookup"><span data-stu-id="ac0fb-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="ac0fb-103">Přidá předávaného typu do tabulky typů daného sestavení.</span><span class="sxs-lookup"><span data-stu-id="ac0fb-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac0fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac0fb-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac0fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac0fb-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="ac0fb-106">Odkaz na sestavení, na které odkazuje předávací typ.</span><span class="sxs-lookup"><span data-stu-id="ac0fb-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ac0fb-107">Plně kvalifikovaný název typu, který se má exportovat</span><span class="sxs-lookup"><span data-stu-id="ac0fb-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ac0fb-108">`ComType`příznaky jako `tdPublic` nebo `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="ac0fb-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="ac0fb-109">Tato hodnota může být předána [metodě DefineExportedType –](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="ac0fb-109">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="ac0fb-110">Přijímá token exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="ac0fb-110">Receives the token of the exported type.</span></span> <span data-ttu-id="ac0fb-111">To je nezbytné jenom pro vygenerování vnořených typů.</span><span class="sxs-lookup"><span data-stu-id="ac0fb-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac0fb-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ac0fb-112">Return Value</span></span>  
 <span data-ttu-id="ac0fb-113">Vrací S_OK, pokud je metoda úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ac0fb-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac0fb-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac0fb-114">Requirements</span></span>  
 <span data-ttu-id="ac0fb-115">Vyžaduje ALink. h</span><span class="sxs-lookup"><span data-stu-id="ac0fb-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac0fb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac0fb-116">See also</span></span>

- [<span data-ttu-id="ac0fb-117">IALink – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac0fb-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ac0fb-118">IALink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac0fb-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ac0fb-119">Rozhraní API ALink</span><span class="sxs-lookup"><span data-stu-id="ac0fb-119">ALink API</span></span>](index.md)
