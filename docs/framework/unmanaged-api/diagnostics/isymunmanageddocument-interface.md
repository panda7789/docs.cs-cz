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
ms.openlocfilehash: 8654f28cc4d82a5ed1419215807ec3360522fd55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="f1250-102">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1250-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="f1250-103">Reprezentuje dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="f1250-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="f1250-104">Dokument je definována uniform resource locator (URL) a typ dokumentu identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="f1250-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="f1250-105">Můžete najít v dokumentu bez ohledu na to, jak je uložen pomocí adresy URL a typu GUID dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f1250-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="f1250-106">Můžete uložit zdrojový dokument do úložiště symbolů a načíst prostřednictvím tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1250-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1250-107">Metody</span><span class="sxs-lookup"><span data-stu-id="f1250-107">Methods</span></span>  
  
|<span data-ttu-id="f1250-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-108">Method</span></span>|<span data-ttu-id="f1250-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f1250-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1250-110">Findclosestline – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="f1250-111">Vrátí nejbližší řádek, který je bod pořadí na základě řádku v tomto dokumentu, který může nebo nemusí být bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="f1250-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="f1250-112">GetCheckSum – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="f1250-113">Získá kontrolního součtu.</span><span class="sxs-lookup"><span data-stu-id="f1250-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="f1250-114">Getchecksumalgorithmid – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="f1250-115">Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.</span><span class="sxs-lookup"><span data-stu-id="f1250-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="f1250-116">Getdocumenttype – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="f1250-117">Získá typ dokumentu tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f1250-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="f1250-118">GetLanguage – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="f1250-119">Získá identifikátor jazyk tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f1250-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="f1250-120">Getlanguagevendor – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="f1250-121">Získá jazyk dodavatele tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f1250-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="f1250-122">Getsourcelength – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="f1250-123">Získá délku, v bajtech embedded zdroje.</span><span class="sxs-lookup"><span data-stu-id="f1250-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="f1250-124">Getsourcerange – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="f1250-125">Vrátí zadaný rozsah embedded zdroje do dané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f1250-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="f1250-126">GetURL – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="f1250-127">Vrátí adresu URL pro tento dokument.</span><span class="sxs-lookup"><span data-stu-id="f1250-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="f1250-128">Hasembeddedsource – metoda</span><span class="sxs-lookup"><span data-stu-id="f1250-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="f1250-129">Vrátí `true` jestli má dokument zdroj vložených v symboly pro ladění; jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="f1250-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1250-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1250-130">See Also</span></span>  
 [<span data-ttu-id="f1250-131">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="f1250-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
