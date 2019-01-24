---
title: ISymUnmanagedDocument – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b14333235882efb6da1ce011c109c67a1d149bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584516"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="f90ca-102">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f90ca-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="f90ca-103">Reprezentuje dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="f90ca-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="f90ca-104">Dokument je definována uniform resource locator (URL) a typu dokumentu identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="f90ca-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="f90ca-105">Můžete vyhledat dokumentu bez ohledu na to, jak se uloží s použitím adresy URL a identifikátor GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f90ca-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="f90ca-106">Můžete ukládat zdrojový dokument v úložišti symbolů a načíst pomocí tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f90ca-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f90ca-107">Metody</span><span class="sxs-lookup"><span data-stu-id="f90ca-107">Methods</span></span>  
  
|<span data-ttu-id="f90ca-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-108">Method</span></span>|<span data-ttu-id="f90ca-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f90ca-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f90ca-110">FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="f90ca-111">Vrátí nejbližší řádek, který je bodu sekvence. Zadaný řádek v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="f90ca-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="f90ca-112">GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="f90ca-113">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="f90ca-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="f90ca-114">GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="f90ca-115">Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="f90ca-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="f90ca-116">GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="f90ca-117">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f90ca-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="f90ca-118">GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="f90ca-119">Získá identifikátor jazyka tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f90ca-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="f90ca-120">GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="f90ca-121">Získá jazyk dodavatele tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f90ca-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="f90ca-122">GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="f90ca-123">Získá délku v bajtech vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="f90ca-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="f90ca-124">GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="f90ca-125">Vrátí zadaný rozsah vloženého zdroje do daného vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f90ca-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="f90ca-126">GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="f90ca-127">Vrátí adresu URL pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="f90ca-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="f90ca-128">HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="f90ca-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="f90ca-129">Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="f90ca-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f90ca-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f90ca-130">See also</span></span>
- [<span data-ttu-id="f90ca-131">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f90ca-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
