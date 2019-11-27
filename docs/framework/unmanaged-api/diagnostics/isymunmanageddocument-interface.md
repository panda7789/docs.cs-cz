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
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449105"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="94ef2-102">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94ef2-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="94ef2-103">Představuje dokument, na který odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="94ef2-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="94ef2-104">Dokument je definován pomocí adresy URL (Uniform Resource Locator) a identifikátoru GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94ef2-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="94ef2-105">Dokument můžete najít bez ohledu na to, jak je uložený, pomocí adresy URL a identifikátoru GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94ef2-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="94ef2-106">Zdroj dokumentu můžete uložit v úložišti symbolů a načíst ho prostřednictvím tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="94ef2-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94ef2-107">Metody</span><span class="sxs-lookup"><span data-stu-id="94ef2-107">Methods</span></span>  
  
|<span data-ttu-id="94ef2-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-108">Method</span></span>|<span data-ttu-id="94ef2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="94ef2-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94ef2-110">FindClosestLine – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="94ef2-111">Vrátí nejbližší řádek, který je sekvenčním bodem, na základě řádku v tomto dokumentu, který může nebo nemusí být bodem sekvence.</span><span class="sxs-lookup"><span data-stu-id="94ef2-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="94ef2-112">GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="94ef2-113">Získá kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="94ef2-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="94ef2-114">GetCheckSumAlgorithmId – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="94ef2-115">Získá identifikátor algoritmu kontrolního součtu nebo vrátí identifikátor GUID všech nul, pokud neexistuje kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="94ef2-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="94ef2-116">GetDocumentType – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="94ef2-117">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94ef2-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="94ef2-118">GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="94ef2-119">Získá identifikátor jazyka tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94ef2-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="94ef2-120">GetLanguageVendor – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="94ef2-121">Získá dodavatele jazyka tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94ef2-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="94ef2-122">GetSourceLength – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="94ef2-123">Získá délku vloženého zdroje v bajtech.</span><span class="sxs-lookup"><span data-stu-id="94ef2-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="94ef2-124">GetSourceRange – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="94ef2-125">Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="94ef2-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="94ef2-126">GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="94ef2-127">Vrátí adresu URL tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94ef2-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="94ef2-128">HasEmbeddedSource – metoda</span><span class="sxs-lookup"><span data-stu-id="94ef2-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="94ef2-129">Vrátí `true`, pokud dokument obsahuje zdrojový vložený v symbolech ladění; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="94ef2-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94ef2-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94ef2-130">See also</span></span>

- [<span data-ttu-id="94ef2-131">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="94ef2-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
