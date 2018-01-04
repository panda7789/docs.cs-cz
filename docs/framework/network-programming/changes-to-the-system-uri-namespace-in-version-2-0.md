---
title: "Změny v oboru názvů System.Uri v verze 2.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3ebf74fbe7f2e207af8bf861efece58026148e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="51225-102">Změny v oboru názvů System.Uri v verze 2.0</span><span class="sxs-lookup"><span data-stu-id="51225-102">Changes to the System.Uri namespace in Version 2.0</span></span>
<span data-ttu-id="51225-103">Bylo provedeno několik změn <xref:System.Uri?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="51225-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="51225-104">Tyto změny pevné nesprávné chování, rozšířeného použitelnost a rozšířené zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="51225-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>  
  
## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="51225-105">Zastaralé a zastaralé členy</span><span class="sxs-lookup"><span data-stu-id="51225-105">Obsolete and Deprecated Members</span></span>  
 <span data-ttu-id="51225-106">Konstruktory:</span><span class="sxs-lookup"><span data-stu-id="51225-106">Constructors:</span></span>  
  
-   <span data-ttu-id="51225-107">Všechny konstruktory, které mají `dontEscape` parametr.</span><span class="sxs-lookup"><span data-stu-id="51225-107">All constructors that have a `dontEscape` parameter.</span></span>  
  
 <span data-ttu-id="51225-108">Metody:</span><span class="sxs-lookup"><span data-stu-id="51225-108">Methods:</span></span>  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a><span data-ttu-id="51225-109">Změny</span><span class="sxs-lookup"><span data-stu-id="51225-109">Changes</span></span>  
  
-   <span data-ttu-id="51225-110">Pro schémata identifikátoru URI, které jsou známé nemá část dotazu (soubor, ftp a dalších) '?' znak je vždy uvozené a nepovažuje začátku <xref:System.Uri.Query%2A> část.</span><span class="sxs-lookup"><span data-stu-id="51225-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>  
  
-   <span data-ttu-id="51225-111">Implicitní souboru identifikátory URI (ve tvaru "c:\directory\file@name.txt"), fragment znak (#) je vždy uvozené Pokud úplné unescaping se požaduje nebo <xref:System.Uri.LocalPath%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="51225-111">For implicit file URIs (of the form "c:\directory\file@name.txt"), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>  
  
-   <span data-ttu-id="51225-112">Odebrala se podpora název hostitele UNC; byla přijata specifikace IDN pro představující mezinárodní názvy hostitelů.</span><span class="sxs-lookup"><span data-stu-id="51225-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>  
  
-   <span data-ttu-id="51225-113"><xref:System.Uri.LocalPath%2A>vždy vrátí hodnotu úplně neuvozené řetězec.</span><span class="sxs-lookup"><span data-stu-id="51225-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>  
  
-   <span data-ttu-id="51225-114"><xref:System.Uri.ToString%2A>není unescape uvozený '%', '?', nebo znakem '#'.</span><span class="sxs-lookup"><span data-stu-id="51225-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>  
  
-   <span data-ttu-id="51225-115"><xref:System.Uri.Equals%2A>nyní zahrnuje <xref:System.Uri.Query%2A> část v kontrole rovnosti.</span><span class="sxs-lookup"><span data-stu-id="51225-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>  
  
-   <span data-ttu-id="51225-116">Operátory "=="a"! =" jsou přepsat a propojit s <xref:System.Uri.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="51225-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>  
  
-   <span data-ttu-id="51225-117"><xref:System.Uri.IsLoopback%2A>nyní vytvoří konzistentních výsledků.</span><span class="sxs-lookup"><span data-stu-id="51225-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>  
  
-   <span data-ttu-id="51225-118">Identifikátor URI "`file:///path`" je už přeložit na "file://path".</span><span class="sxs-lookup"><span data-stu-id="51225-118">The URI "`file:///path`" is no longer translated into "file://path".</span></span>  
  
-   <span data-ttu-id="51225-119">"#" teď považována za zakončením název hostitele.</span><span class="sxs-lookup"><span data-stu-id="51225-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="51225-120">Tedy "http://consoto.com#fragment" teď převést na "http://contoso.com/#fragment".</span><span class="sxs-lookup"><span data-stu-id="51225-120">That is, "http://consoto.com#fragment" is now converted to "http://contoso.com/#fragment".</span></span>  
  
-   <span data-ttu-id="51225-121">Chyby při kombinování základní identifikátor URI s fragment byl opraven.</span><span class="sxs-lookup"><span data-stu-id="51225-121">A bug when combining a base URI with a fragment has been fixed.</span></span>  
  
-   <span data-ttu-id="51225-122">Chyby v <xref:System.Uri.HostNameType%2A> vyřešen.</span><span class="sxs-lookup"><span data-stu-id="51225-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>  
  
-   <span data-ttu-id="51225-123">Chyby při analýze NNTP vyřešen.</span><span class="sxs-lookup"><span data-stu-id="51225-123">A bug in NNTP parsing is fixed.</span></span>  
  
-   <span data-ttu-id="51225-124">Identifikátor URI ve tvaru HTTP:contoso.com nyní vyhodí výjimku analýzy.</span><span class="sxs-lookup"><span data-stu-id="51225-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>  
  
-   <span data-ttu-id="51225-125">Rozhraní Framework správně zpracovává informací o uživateli v identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="51225-125">The Framework correctly handles userinfo in a URI.</span></span>  
  
-   <span data-ttu-id="51225-126">Identifikátor URI cesta komprese vyřešen tak, aby porušený identifikátor URI nelze procházet systému souborů výše kořenu.</span><span class="sxs-lookup"><span data-stu-id="51225-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51225-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="51225-127">See Also</span></span>  
 <xref:System.Uri?displayProperty=nameWithType>
