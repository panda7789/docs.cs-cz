---
title: "Rozhraní úložiště symbolů diagnostiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50ef54c90609bf8ef1e3a943664daef95f50d926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="8689d-102">Rozhraní úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8689d-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="8689d-103">Toto téma popisuje nespravovaná rozhraní, které umožňují kompilátoru ke generování informací o symbolu za účelem použití ladicí program.</span><span class="sxs-lookup"><span data-stu-id="8689d-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8689d-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8689d-104">In This Section</span></span>  
 [<span data-ttu-id="8689d-105">Ibindingdisplay – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="8689d-106">Poskytuje metody, které zobrazují aktuální informace o vazbě o běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8689d-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="8689d-107">Idebugautoattach – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="8689d-108">Definuje rozhraní pro připojení serveru vyvolá ladicí program automaticky.</span><span class="sxs-lookup"><span data-stu-id="8689d-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="8689d-109">Inotifyconnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="8689d-110">Deklaruje metody pro registraci a zrušení registrace oznámení zdroj připojení.</span><span class="sxs-lookup"><span data-stu-id="8689d-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="8689d-111">Inotifysink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="8689d-112">Deklaruje metody pro podřízený oznámení.</span><span class="sxs-lookup"><span data-stu-id="8689d-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="8689d-113">Inotifysource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="8689d-114">Deklaruje metodu pro nastavení oznámení filtry.</span><span class="sxs-lookup"><span data-stu-id="8689d-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="8689d-115">Isymencunmanagedmethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="8689d-116">Obsahuje informace o funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="8689d-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="8689d-117">Isymunmanagedasyncmethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="8689d-118">Toto rozhraní je doplňkovým čtení na [isymunmanagedasyncmethodpropertieswriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8689d-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="8689d-119">Isymunmanagedasyncmethodpropertieswriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="8689d-120">Umožňuje definici volitelné asynchronní metoda informace za metoda symbol.</span><span class="sxs-lookup"><span data-stu-id="8689d-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="8689d-121">Musíte použít s otevřenou metodu (to znamená, mezi volání [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="8689d-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="8689d-122">Isymunmanagedbinder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="8689d-123">Představuje vazač symbol pro nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="8689d-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="8689d-124">Isymunmanagedbinder2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="8689d-125">Představuje vazač symbol pro nespravovaného kódu a rozšiřuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8689d-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="8689d-126">Isymunmanagedbinder3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="8689d-127">Představuje vazač symbol pro nespravovaného kódu a rozšiřuje `ISymUnmanagedBinder` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8689d-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="8689d-128">ISymUnmanagedConstant – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="8689d-129">Poskytuje přístup k nespravované konstanty.</span><span class="sxs-lookup"><span data-stu-id="8689d-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="8689d-130">Isymunmanageddispose – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="8689d-131">Uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="8689d-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="8689d-132">ISymUnmanagedDocument – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="8689d-133">Reprezentuje dokument odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="8689d-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="8689d-134">Isymunmanageddocumentwriter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="8689d-135">Poskytuje metody pro zápis do dokumentu odkazuje úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="8689d-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="8689d-136">Isymunmanagedencupdate – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="8689d-137">Poskytuje metody pro funkci upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="8689d-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="8689d-138">ISymUnmanagedMethod – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="8689d-139">Představuje metodu v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="8689d-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="8689d-140">ISymUnmanagedNamespace – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="8689d-141">Představuje obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8689d-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="8689d-142">ISymUnmanagedReader – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="8689d-143">Představuje čtečku symbol, který poskytuje přístup k dokumentům, metod a proměnné v rámci úložiště symbolů.</span><span class="sxs-lookup"><span data-stu-id="8689d-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="8689d-144">Isymunmanagedreader2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="8689d-145">Získá metody čtečky symbol daného token metoda a číslo verze úpravy a kopie.</span><span class="sxs-lookup"><span data-stu-id="8689d-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="8689d-146">Isymunmanagedreadersymbolsearchinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="8689d-147">Poskytuje metody, které získání informací o symbolu vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="8689d-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="8689d-148">ISymUnmanagedScope – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="8689d-149">Představuje lexikální obor v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="8689d-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="8689d-150">Isymunmanagedscope2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="8689d-151">Představuje lexikální obor v rámci metody a rozšiřuje `ISymUnmanagedScope` rozhraní s metody, které získat informace o konstanty definované v rámci oboru...</span><span class="sxs-lookup"><span data-stu-id="8689d-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="8689d-152">Isymunmanagedsourceservermodule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="8689d-153">Pro modul poskytuje data zdrojového serveru.</span><span class="sxs-lookup"><span data-stu-id="8689d-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="8689d-154">Isymunmanagedsymbolsearchinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="8689d-155">Poskytuje metody, které získat informace o cestě pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="8689d-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="8689d-156">ISymUnmanagedVariable – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="8689d-157">Představuje proměnnou, třeba parametr, místní proměnné nebo pole.</span><span class="sxs-lookup"><span data-stu-id="8689d-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="8689d-158">ISymUnmanagedWriter – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="8689d-159">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="8689d-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="8689d-160">Isymunmanagedwriter2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="8689d-161">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="8689d-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="8689d-162">Rozšiřuje `ISymUnmanagedWriter` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8689d-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="8689d-163">ISymUnmanagedWriter3 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="8689d-164">Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.</span><span class="sxs-lookup"><span data-stu-id="8689d-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="8689d-165">Rozšiřuje `ISymUnmanagedWriter` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8689d-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="8689d-166">Isymunmanagedwriter4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="8689d-167">Isymunmanagedwriter4 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8689d-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="8689d-168">Isymunmanagedwriter5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8689d-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="8689d-169">Isymunmanagedwriter5 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8689d-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8689d-170">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8689d-170">Related Sections</span></span>  
 [<span data-ttu-id="8689d-171">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8689d-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="8689d-172">Struktury úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="8689d-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="8689d-173">Ladění</span><span class="sxs-lookup"><span data-stu-id="8689d-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
