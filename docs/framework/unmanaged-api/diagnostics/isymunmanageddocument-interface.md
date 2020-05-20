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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615563"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="6e1c5-102">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e1c5-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="6e1c5-103">Představuje dokument, na který odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="6e1c5-104">Dokument je definován pomocí adresy URL (Uniform Resource Locator) a identifikátoru GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="6e1c5-105">Dokument můžete najít bez ohledu na to, jak je uložený, pomocí adresy URL a identifikátoru GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="6e1c5-106">Zdroj dokumentu můžete uložit v úložišti symbolů a načíst ho prostřednictvím tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e1c5-107">Metody</span><span class="sxs-lookup"><span data-stu-id="6e1c5-107">Methods</span></span>  
  
|<span data-ttu-id="6e1c5-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-108">Method</span></span>|<span data-ttu-id="6e1c5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6e1c5-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e1c5-110">FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-110">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="6e1c5-111">Vrátí nejbližší řádek, který je sekvenčním bodem, na základě řádku v tomto dokumentu, který může nebo nemusí být bodem sekvence.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="6e1c5-112">GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-112">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="6e1c5-113">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="6e1c5-114">GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-114">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="6e1c5-115">Získá identifikátor algoritmu kontrolního součtu nebo vrátí identifikátor GUID všech nul, pokud neexistuje kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="6e1c5-116">GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-116">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="6e1c5-117">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="6e1c5-118">GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-118">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="6e1c5-119">Získá identifikátor jazyka tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="6e1c5-120">GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-120">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="6e1c5-121">Získá dodavatele jazyka tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="6e1c5-122">GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-122">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="6e1c5-123">Získá délku vloženého zdroje v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="6e1c5-124">GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-124">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="6e1c5-125">Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="6e1c5-126">GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-126">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="6e1c5-127">Vrátí adresu URL tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6e1c5-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="6e1c5-128">HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c5-128">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="6e1c5-129">Vrátí, `true` zda má dokument ve symbolech ladění zdroj vložený. v opačném případě vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="6e1c5-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e1c5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e1c5-130">See also</span></span>

- [<span data-ttu-id="6e1c5-131">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="6e1c5-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
