---
title: Rozhraní úložiště symbolů diagnostiky
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787891"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="05819-102">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="05819-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="05819-103">Toto téma popisuje nespravovaná rozhraní, které umožňují kompilátoru generovat informace o symbolech pro použití ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="05819-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05819-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="05819-104">In This Section</span></span>  
 [<span data-ttu-id="05819-105">IBindingDisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="05819-106">Poskytuje metody, které zobrazení aktuální vazby informací o spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="05819-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="05819-107">IDebugAutoAttach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="05819-108">Definuje rozhraní pro automatické serveru vyvolá ladicí program připojit.</span><span class="sxs-lookup"><span data-stu-id="05819-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="05819-109">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="05819-110">Deklaruje metody pro registraci a zrušení registrace oznámení zdroj připojení.</span><span class="sxs-lookup"><span data-stu-id="05819-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="05819-111">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="05819-112">Deklaruje metody pro jímku oznámení.</span><span class="sxs-lookup"><span data-stu-id="05819-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="05819-113">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="05819-114">Deklaruje metodu pro nastavení oznámení filtrů.</span><span class="sxs-lookup"><span data-stu-id="05819-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="05819-115">ISymENCUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="05819-116">Obsahuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="05819-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="05819-117">ISymUnmanagedAsyncMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="05819-118">Toto rozhraní je doplněk čtení k [isymunmanagedasyncmethodpropertieswriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="05819-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="05819-119">ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="05819-120">Umožňuje definici volitelné asynchronní metoda informace o metoda symbol.</span><span class="sxs-lookup"><span data-stu-id="05819-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="05819-121">Musíte použít s metodou otevřené (tedy mezi voláními [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="05819-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="05819-122">ISymUnmanagedBinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="05819-123">Představuje vazač symbolů pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="05819-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="05819-124">ISymUnmanagedBinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="05819-125">Představuje vazač symbolů pro nespravovaný kód a rozšiřuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05819-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="05819-126">ISymUnmanagedBinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="05819-127">Představuje vazač symbolů pro nespravovaný kód a rozšiřuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05819-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="05819-128">ISymUnmanagedConstant – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="05819-129">Poskytuje přístup k nespravované konstanty.</span><span class="sxs-lookup"><span data-stu-id="05819-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="05819-130">ISymUnmanagedDispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="05819-131">Uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="05819-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="05819-132">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="05819-133">Reprezentuje dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="05819-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="05819-134">ISymUnmanagedDocumentWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="05819-135">Poskytuje metody pro zápis na dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="05819-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="05819-136">ISymUnmanagedENCUpdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="05819-137">Poskytuje metody pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="05819-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="05819-138">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="05819-139">Představuje metodu v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="05819-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="05819-140">ISymUnmanagedNamespace – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="05819-141">Představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="05819-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="05819-142">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="05819-143">Představuje modul pro načítání symbolů, který poskytuje přístup k dokumentům, metody a proměnných v úložišti symbolů.</span><span class="sxs-lookup"><span data-stu-id="05819-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="05819-144">ISymUnmanagedReader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="05819-145">Získá token metody a číslo verze upravit a kopírovat metodu čtečky symbolů.</span><span class="sxs-lookup"><span data-stu-id="05819-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="05819-146">ISymUnmanagedReaderSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="05819-147">Poskytuje metody, které získávají informace hledání symbolu.</span><span class="sxs-lookup"><span data-stu-id="05819-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="05819-148">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="05819-149">Představuje lexikální rozsah v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="05819-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="05819-150">ISymUnmanagedScope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="05819-151">Představuje lexikální rozsah v rámci metody a rozšiřuje `ISymUnmanagedScope` rozhraní s metodami, které získávají informace o konstanty definované v rámci oboru...</span><span class="sxs-lookup"><span data-stu-id="05819-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="05819-152">ISymUnmanagedSourceServerModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="05819-153">Pro modul poskytuje data zdrojového serveru.</span><span class="sxs-lookup"><span data-stu-id="05819-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="05819-154">ISymUnmanagedSymbolSearchInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="05819-155">Poskytuje metody, které získáte informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="05819-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="05819-156">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="05819-157">Představuje proměnnou, jako je například parametr, místní proměnné nebo pole.</span><span class="sxs-lookup"><span data-stu-id="05819-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="05819-158">ISymUnmanagedWriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="05819-159">Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.</span><span class="sxs-lookup"><span data-stu-id="05819-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="05819-160">ISymUnmanagedWriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="05819-161">Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.</span><span class="sxs-lookup"><span data-stu-id="05819-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="05819-162">Rozšiřuje `ISymUnmanagedWriter` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05819-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="05819-163">ISymUnmanagedWriter3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="05819-164">Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.</span><span class="sxs-lookup"><span data-stu-id="05819-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="05819-165">Rozšiřuje `ISymUnmanagedWriter` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05819-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="05819-166">ISymUnmanagedWriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="05819-167">Isymunmanagedwriter4 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05819-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="05819-168">ISymUnmanagedWriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05819-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="05819-169">Isymunmanagedwriter5 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05819-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05819-170">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="05819-170">Related Sections</span></span>  
 [<span data-ttu-id="05819-171">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="05819-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="05819-172">Struktury pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="05819-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="05819-173">Ladění</span><span class="sxs-lookup"><span data-stu-id="05819-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
