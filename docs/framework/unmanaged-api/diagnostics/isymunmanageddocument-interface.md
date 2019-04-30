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
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939773"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="380c3-102">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="380c3-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="380c3-103">Reprezentuje dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="380c3-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="380c3-104">Dokument je definována uniform resource locator (URL) a typu dokumentu identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="380c3-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="380c3-105">Můžete vyhledat dokumentu bez ohledu na to, jak se uloží s použitím adresy URL a identifikátor GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="380c3-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="380c3-106">Můžete ukládat zdrojový dokument v úložišti symbolů a načíst pomocí tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="380c3-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="380c3-107">Metody</span><span class="sxs-lookup"><span data-stu-id="380c3-107">Methods</span></span>  
  
|<span data-ttu-id="380c3-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-108">Method</span></span>|<span data-ttu-id="380c3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="380c3-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="380c3-110">FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="380c3-111">Vrátí nejbližší řádek, který je bodu sekvence. Zadaný řádek v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="380c3-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="380c3-112">GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="380c3-113">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="380c3-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="380c3-114">GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="380c3-115">Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="380c3-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="380c3-116">GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="380c3-117">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="380c3-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="380c3-118">GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="380c3-119">Získá identifikátor jazyka tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="380c3-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="380c3-120">GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="380c3-121">Získá jazyk dodavatele tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="380c3-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="380c3-122">GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="380c3-123">Získá délku v bajtech vloženého zdroje.</span><span class="sxs-lookup"><span data-stu-id="380c3-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="380c3-124">GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="380c3-125">Vrátí zadaný rozsah vloženého zdroje do daného vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="380c3-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="380c3-126">GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="380c3-127">Vrátí adresu URL pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="380c3-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="380c3-128">HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="380c3-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="380c3-129">Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="380c3-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="380c3-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="380c3-130">See also</span></span>

- [<span data-ttu-id="380c3-131">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="380c3-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
