---
title: Změny oboru názvů System.Uri ve verzi 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
ms.openlocfilehash: 987010b8367069e8089df3f809d23f258bb68f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642760"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="c7bed-102">Změny oboru názvů System.Uri ve verzi 2.0</span><span class="sxs-lookup"><span data-stu-id="c7bed-102">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="c7bed-103">Ve <xref:System.Uri?displayProperty=nameWithType> třídě bylo provedeno několik změn.</span><span class="sxs-lookup"><span data-stu-id="c7bed-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c7bed-104">Tyto změny opravily nesprávné chování, lepší použitelnost a rozšířené zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c7bed-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="c7bed-105">Zastaralí a zastaralí členové</span><span class="sxs-lookup"><span data-stu-id="c7bed-105">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="c7bed-106">Konstruktory:</span><span class="sxs-lookup"><span data-stu-id="c7bed-106">Constructors:</span></span>

- <span data-ttu-id="c7bed-107">Všechny konstruktory, `dontEscape` které mají parametr.</span><span class="sxs-lookup"><span data-stu-id="c7bed-107">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="c7bed-108">Metody:</span><span class="sxs-lookup"><span data-stu-id="c7bed-108">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="c7bed-109">Změny</span><span class="sxs-lookup"><span data-stu-id="c7bed-109">Changes</span></span>

- <span data-ttu-id="c7bed-110">U schémat URI, o kterých je známo, že nemají část dotazu (soubor, ftp a další), <xref:System.Uri.Query%2A> je znak '?' vždy uvozen a není považován za začátek dílu.</span><span class="sxs-lookup"><span data-stu-id="c7bed-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="c7bed-111">Pro implicitní soubor URI `c:\directory\file@name.txt`(formuláře ) znak fragmentu ('#') je vždy <xref:System.Uri.LocalPath%2A> uvozen, pokud není požadováno úplné neuvození nebo není `true`.</span><span class="sxs-lookup"><span data-stu-id="c7bed-111">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="c7bed-112">Podpora názvu hostitele UNC byla odebrána. byla přijata specifikace IDN pro zastupování mezinárodních názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="c7bed-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="c7bed-113"><xref:System.Uri.LocalPath%2A>vždy vrátí zcela unescaped řetězec.</span><span class="sxs-lookup"><span data-stu-id="c7bed-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="c7bed-114"><xref:System.Uri.ToString%2A>neunescape uvozený znak %, '?' nebo '#'.</span><span class="sxs-lookup"><span data-stu-id="c7bed-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="c7bed-115"><xref:System.Uri.Equals%2A>nyní zahrnuje <xref:System.Uri.Query%2A> část kontroly rovnosti.</span><span class="sxs-lookup"><span data-stu-id="c7bed-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="c7bed-116">Operátory "==" a "!=" jsou <xref:System.Uri.Equals%2A> přepsány a propojeny s metodou.</span><span class="sxs-lookup"><span data-stu-id="c7bed-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="c7bed-117"><xref:System.Uri.IsLoopback%2A>nyní vytváří konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="c7bed-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="c7bed-118">Identifikátor URI`file:///path`" " již `file://path`není přeložen do .</span><span class="sxs-lookup"><span data-stu-id="c7bed-118">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="c7bed-119">"#" je nyní rozpoznán jako zakončení názvu hostitele.</span><span class="sxs-lookup"><span data-stu-id="c7bed-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="c7bed-120">To znamená, `http://contoso.com#fragment` že je `http://contoso.com/#fragment`nyní převeden na .</span><span class="sxs-lookup"><span data-stu-id="c7bed-120">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="c7bed-121">Byla opravena chyba při kombinování základního identifikátoru URI s fragmentem.</span><span class="sxs-lookup"><span data-stu-id="c7bed-121">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="c7bed-122">Chyba je <xref:System.Uri.HostNameType%2A> opravena.</span><span class="sxs-lookup"><span data-stu-id="c7bed-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="c7bed-123">Chyba v analýzě NNTP je pevná.</span><span class="sxs-lookup"><span data-stu-id="c7bed-123">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="c7bed-124">Identifikátor URI formuláře HTTP:contoso.com nyní vyvolá výjimku analýzy.</span><span class="sxs-lookup"><span data-stu-id="c7bed-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="c7bed-125">Rozhraní Framework správně zpracovává userinfo v uri.</span><span class="sxs-lookup"><span data-stu-id="c7bed-125">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="c7bed-126">Komprese cesty URI je opravena tak, že přerušený identifikátor URI nemůže procházet systémem souborů nad kořenem.</span><span class="sxs-lookup"><span data-stu-id="c7bed-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7bed-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7bed-127">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
