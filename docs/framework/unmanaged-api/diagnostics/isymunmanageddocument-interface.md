---
title: "ISymUnmanagedDocument – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument
helpviewer_keywords: ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="11fb9-102">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11fb9-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="11fb9-103">Reprezentuje dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="11fb9-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="11fb9-104">Dokument je definována uniform resource locator (URL) a typ dokumentu identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="11fb9-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="11fb9-105">Můžete najít v dokumentu bez ohledu na to, jak je uložen pomocí adresy URL a typu GUID dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11fb9-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="11fb9-106">Můžete uložit zdrojový dokument do úložiště symbolů a načíst prostřednictvím tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="11fb9-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11fb9-107">Metody</span><span class="sxs-lookup"><span data-stu-id="11fb9-107">Methods</span></span>  
  
|<span data-ttu-id="11fb9-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-108">Method</span></span>|<span data-ttu-id="11fb9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="11fb9-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11fb9-110">FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="11fb9-111">Vrátí nejbližší řádek, který je bod pořadí na základě řádku v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="11fb9-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="11fb9-112">GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="11fb9-113">Získá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="11fb9-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="11fb9-114">GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="11fb9-115">Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="11fb9-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="11fb9-116">GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="11fb9-117">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11fb9-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="11fb9-118">GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="11fb9-119">Získá identifikátor jazyk tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11fb9-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="11fb9-120">GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="11fb9-121">Získá jazyk dodavatele tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="11fb9-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="11fb9-122">GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="11fb9-123">Získá délku, v bajtech embedded zdroje.</span><span class="sxs-lookup"><span data-stu-id="11fb9-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="11fb9-124">GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="11fb9-125">Vrátí zadaný rozsah embedded zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="11fb9-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="11fb9-126">GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="11fb9-127">Vrátí adresu URL pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="11fb9-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="11fb9-128">HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="11fb9-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="11fb9-129">Vrátí `true` jestli má dokument zdroj vložených v symboly pro ladění; jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="11fb9-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11fb9-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="11fb9-130">See Also</span></span>  
 [<span data-ttu-id="11fb9-131">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="11fb9-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
