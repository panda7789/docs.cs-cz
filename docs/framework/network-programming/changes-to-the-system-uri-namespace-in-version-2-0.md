---
title: Změny v oboru názvů System.Uri ve verzi 2.0
ms.date: 03/30/2017
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f300ab05f28feca8baa13c4078df622e1e7d9d19
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479770"
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a><span data-ttu-id="a9175-102">Změny v oboru názvů System.Uri ve verzi 2.0</span><span class="sxs-lookup"><span data-stu-id="a9175-102">Changes to the System.Uri namespace in version 2.0</span></span>

<span data-ttu-id="a9175-103">Bylo provedeno několik změn <xref:System.Uri?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="a9175-103">Several changes were made to the <xref:System.Uri?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a9175-104">Tyto změny oprava nesprávné chování, rozšířeného použitelnost a zvýšené zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a9175-104">These changes fixed incorrect behavior, enhanced usability, and enhanced security.</span></span>

## <a name="obsolete-and-deprecated-members"></a><span data-ttu-id="a9175-105">Zastaralé a již zastaralé členy</span><span class="sxs-lookup"><span data-stu-id="a9175-105">Obsolete and deprecated Members</span></span>

 <span data-ttu-id="a9175-106">Konstruktory:</span><span class="sxs-lookup"><span data-stu-id="a9175-106">Constructors:</span></span>

- <span data-ttu-id="a9175-107">Všechny konstruktory, které mají `dontEscape` parametru.</span><span class="sxs-lookup"><span data-stu-id="a9175-107">All constructors that have a `dontEscape` parameter.</span></span>

 <span data-ttu-id="a9175-108">Metody:</span><span class="sxs-lookup"><span data-stu-id="a9175-108">Methods:</span></span>

- <xref:System.Uri.CheckSecurity%2A>

- <xref:System.Uri.Escape%2A>

- <xref:System.Uri.Canonicalize%2A>

- <xref:System.Uri.Parse%2A>

- <xref:System.Uri.IsReservedCharacter%2A>

- <xref:System.Uri.IsBadFileSystemCharacter%2A>

- <xref:System.Uri.IsExcludedCharacter%2A>

- <xref:System.Uri.EscapeString%2A>

## <a name="changes"></a><span data-ttu-id="a9175-109">Změny</span><span class="sxs-lookup"><span data-stu-id="a9175-109">Changes</span></span>

- <span data-ttu-id="a9175-110">Pro schémata identifikátoru URI, které se ví, že není nutné část dotazu (souboru, protokolu ftp a dalších) "?" znak je vždy uvozen řídicími znaky a není považováno za začátek <xref:System.Uri.Query%2A> část.</span><span class="sxs-lookup"><span data-stu-id="a9175-110">For URI schemes that are known to not have a query part (file, ftp, and others), the '?' character is always escaped and is not considered the beginning of a <xref:System.Uri.Query%2A> part.</span></span>

- <span data-ttu-id="a9175-111">Implicitní souboru identifikátory URI (ve formátu `c:\directory\file@name.txt`), fragment znak (#) je vždy uvozen řídicími znaky, pokud je požadována úplná unescaping nebo <xref:System.Uri.LocalPath%2A> je `true`.</span><span class="sxs-lookup"><span data-stu-id="a9175-111">For implicit file URIs (of the form `c:\directory\file@name.txt`), the fragment character ('#') is always escaped unless full unescaping is requested or <xref:System.Uri.LocalPath%2A> is `true`.</span></span>

- <span data-ttu-id="a9175-112">Byla odebrána podpora UNC hostname; byla přijata specifikaci IDN představující mezinárodní názvy hostitelů.</span><span class="sxs-lookup"><span data-stu-id="a9175-112">UNC hostname support was removed; the IDN specification for representing international hostnames was adopted.</span></span>

- <span data-ttu-id="a9175-113"><xref:System.Uri.LocalPath%2A> vždy vrátí řetězec zcela bez řídících znaků.</span><span class="sxs-lookup"><span data-stu-id="a9175-113"><xref:System.Uri.LocalPath%2A> always returns a completely unescaped string.</span></span>

- <span data-ttu-id="a9175-114"><xref:System.Uri.ToString%2A> není unescape s uvozovacími znaky "%", "?", nebo znak "#".</span><span class="sxs-lookup"><span data-stu-id="a9175-114"><xref:System.Uri.ToString%2A> does not unescape an escaped '%', '?', or '#' character.</span></span>

- <span data-ttu-id="a9175-115"><xref:System.Uri.Equals%2A> nyní zahrnuje <xref:System.Uri.Query%2A> část v kontrole rovnosti.</span><span class="sxs-lookup"><span data-stu-id="a9175-115"><xref:System.Uri.Equals%2A> now includes the <xref:System.Uri.Query%2A> part in the equality check.</span></span>

- <span data-ttu-id="a9175-116">Operátory "=="a"! =" jsou přepsat a že propojení se <xref:System.Uri.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a9175-116">Operators "==" and "!=" are overridden and linked to the <xref:System.Uri.Equals%2A> method.</span></span>

- <span data-ttu-id="a9175-117"><xref:System.Uri.IsLoopback%2A> nyní poskytuje konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="a9175-117"><xref:System.Uri.IsLoopback%2A> now produces consistent results.</span></span>

- <span data-ttu-id="a9175-118">Identifikátor URI "`file:///path`" je již přeloženy do `file://path`.</span><span class="sxs-lookup"><span data-stu-id="a9175-118">The URI "`file:///path`" is no longer translated into `file://path`.</span></span>

- <span data-ttu-id="a9175-119">"#" nyní považována za zakončením název hostitele.</span><span class="sxs-lookup"><span data-stu-id="a9175-119">"#" is now recognized as a host name terminator.</span></span> <span data-ttu-id="a9175-120">To znamená `http://contoso.com#fragment` je nyní převést na `http://contoso.com/#fragment`.</span><span class="sxs-lookup"><span data-stu-id="a9175-120">That is, `http://contoso.com#fragment` is now converted to `http://contoso.com/#fragment`.</span></span>

- <span data-ttu-id="a9175-121">Opravili jsme chybu při kombinování základní identifikátor URI s fragmentem.</span><span class="sxs-lookup"><span data-stu-id="a9175-121">A bug when combining a base URI with a fragment has been fixed.</span></span>

- <span data-ttu-id="a9175-122">Chyba v <xref:System.Uri.HostNameType%2A> vyřešen.</span><span class="sxs-lookup"><span data-stu-id="a9175-122">A bug in <xref:System.Uri.HostNameType%2A> is fixed.</span></span>

- <span data-ttu-id="a9175-123">Chyba při analýze NNTP opravena.</span><span class="sxs-lookup"><span data-stu-id="a9175-123">A bug in NNTP parsing is fixed.</span></span>

- <span data-ttu-id="a9175-124">Identifikátor URI ve formátu HTTP:contoso.com nyní výjimku analýzy.</span><span class="sxs-lookup"><span data-stu-id="a9175-124">A URI of the form HTTP:contoso.com now throws a parsing exception.</span></span>

- <span data-ttu-id="a9175-125">Rozhraní správně zpracovává informací o uživateli v identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="a9175-125">The Framework correctly handles userinfo in a URI.</span></span>

- <span data-ttu-id="a9175-126">Komprese cesty identifikátoru URI je vyřešen tak, aby přerušení identifikátor URI nelze procházení systému souborů kořenem.</span><span class="sxs-lookup"><span data-stu-id="a9175-126">URI path compression is fixed so that a broken URI cannot traverse the file system above the root.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9175-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9175-127">See also</span></span>

- <xref:System.Uri?displayProperty=nameWithType>
