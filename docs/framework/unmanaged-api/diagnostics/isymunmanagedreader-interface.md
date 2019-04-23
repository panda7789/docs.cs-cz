---
title: ISymUnmanagedReader – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0782533f773b69eeeb0b89175e5b22c61e822ed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147209"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="61f21-102">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61f21-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="61f21-103">Představuje modul pro načítání symbolů, který poskytuje přístup k dokumentům, metody a proměnných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="61f21-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61f21-104">Metody</span><span class="sxs-lookup"><span data-stu-id="61f21-104">Methods</span></span>  
  
|<span data-ttu-id="61f21-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-105">Method</span></span>|<span data-ttu-id="61f21-106">Popis</span><span class="sxs-lookup"><span data-stu-id="61f21-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61f21-107">GetDocument – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="61f21-108">Najde dokument.</span><span class="sxs-lookup"><span data-stu-id="61f21-108">Finds a document.</span></span>|  
|[<span data-ttu-id="61f21-109">GetDocuments – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="61f21-110">Vrací pole všech dokumentů, které jsou definovány v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="61f21-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="61f21-111">GetDocumentVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="61f21-112">Načte zadanou verzi zadaný dokument.</span><span class="sxs-lookup"><span data-stu-id="61f21-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="61f21-113">GetGlobalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="61f21-114">Vrátí všechny globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="61f21-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="61f21-115">GetMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="61f21-116">Získá metodu čtečky symbolů daný token metody.</span><span class="sxs-lookup"><span data-stu-id="61f21-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="61f21-117">GetMethodByVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="61f21-118">Získá metodu čtečky symbolů daný token metody a číslo verze upravit a kopírovat.</span><span class="sxs-lookup"><span data-stu-id="61f21-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="61f21-119">GetMethodFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="61f21-120">Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="61f21-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="61f21-121">GetMethodsFromDocumentPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="61f21-122">Vrátí pole z metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="61f21-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="61f21-123">GetMethodVersion – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="61f21-124">Získá verzi metody.</span><span class="sxs-lookup"><span data-stu-id="61f21-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="61f21-125">GetNamespaces – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="61f21-126">Získá oborů názvů definovaných v globálním oboru v rámci tohoto úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="61f21-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="61f21-127">GetSymAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="61f21-128">Získá vlastní atribut na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="61f21-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="61f21-129">GetSymbolStoreFileName – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="61f21-130">Poskytuje název souboru na disku úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="61f21-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="61f21-131">GetUserEntryPoint – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="61f21-132">Vrátí metodu, která byla zadána jako uživatel vstupní bod pro modul, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="61f21-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="61f21-133">GetVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="61f21-134">Vrátíte jiné než místní proměnné, jeho nadřazený a název.</span><span class="sxs-lookup"><span data-stu-id="61f21-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="61f21-135">Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="61f21-136">Inicializuje modul pro načítání symbolů rozhraní programu pro import metadat, která tento čtecí bude spojená s, spolu s názvem souboru modulu.</span><span class="sxs-lookup"><span data-stu-id="61f21-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="61f21-137">ReplaceSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="61f21-138">Nahradí existující úložiště symbolů do úložiště symbolů delta.</span><span class="sxs-lookup"><span data-stu-id="61f21-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="61f21-139">UpdateSymbolStore – metoda</span><span class="sxs-lookup"><span data-stu-id="61f21-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="61f21-140">Aktualizuje existující úložiště symbolů do úložiště symbolů delta.</span><span class="sxs-lookup"><span data-stu-id="61f21-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61f21-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61f21-141">Requirements</span></span>  
 <span data-ttu-id="61f21-142">**Záhlaví:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61f21-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f21-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61f21-143">See also</span></span>

- [<span data-ttu-id="61f21-144">Rozhraní pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="61f21-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="61f21-145">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61f21-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
