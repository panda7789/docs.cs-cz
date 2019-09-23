---
title: Přehled gRPC-gRPC pro vývojáře WCF
description: Seznamte se se sadou principů, které vyvíjejí vývoj gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b372cc9dcdb2efd605b3d9b688513e4ff8530b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184440"
---
# <a name="grpc-overview"></a><span data-ttu-id="f8ca6-103">gRPC – přehled</span><span class="sxs-lookup"><span data-stu-id="f8ca6-103">gRPC overview</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f8ca6-104">Po zobrazení genesisy WCF a gRPC v poslední kapitole bude tato kapitola brát v úvahu některé klíčové funkce gRPC a jejich porovnání s WCF.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-104">After looking at the genesis of both WCF and gRPC in the last chapter, this chapter will consider some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="f8ca6-105">ASP.NET Core 3,0 je první verze ASP.NET, která nativně podporuje gRPC jako občana první třídy, s týmy Microsoftu, které přispívají k oficiální implementaci rozhraní .NET gRPC.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="f8ca6-106">Doporučuje se jako nejlepší přístup pro vytváření distribuovaných aplikací s .NET, které mohou spolupracovat se všemi ostatními hlavními programovacími jazyky a architekturami.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-106">It's recommended as the best approach for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="f8ca6-107">Klíč zásad</span><span class="sxs-lookup"><span data-stu-id="f8ca6-107">Key principles</span></span>

<span data-ttu-id="f8ca6-108">Jak je popsáno v kapitole 1, Google chtěla použít zavedení HTTP/2 pro repráci Stubby, její interní infrastrukturu RPC pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to rework Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="f8ca6-109">Stubby, přejmenované gRPC, teď můžou využít standardizaci a by rozšířila její použitelnost na Mobile Computing, Cloud a Internet věcí.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-109">Stubby, renamed gRPC, now could take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="f8ca6-110">Za tímto účelem vytvořila sada [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) sadu principů, které by se řídily gRPC.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-110">To achieve this, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="f8ca6-111">V následujícím seznamu jsou uvedeny nejdůležitější ty, které se hlavně týkají maximalizace usnadnění přístupu a použitelnosti:</span><span class="sxs-lookup"><span data-stu-id="f8ca6-111">The following list shows the most relevant ones, which are mainly concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="f8ca6-112">**Free a Open** – všechny artefakty by měly být open source s licencováním, které nebrání vývojářům v přijímání gRPC.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-112">**Free and open** – all artifacts should be open source with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="f8ca6-113">**Pokrytí a jednoduchost** – gRPC by měly být k dispozici napříč všemi oblíbenými platformami a dostatečně snadno, aby je bylo možné vytvářet na jakékoli platformě.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-113">**Coverage and simplicity** – gRPC should be available across every popular platform and simple enough to build on any platform.</span></span>
- <span data-ttu-id="f8ca6-114">**Interoperabilita a dosah** – je vhodné používat gRPC v libovolné síti, bez ohledu na šířku pásma nebo latenci, a to s využitím široce dostupných síťových standardů.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-114">**Interoperability and reach** – it should be possible to use gRPC on any network, regardless of bandwidth or latency, using widely available network standards.</span></span>
- <span data-ttu-id="f8ca6-115">**Obecný účel a** výkon – rozhraní by mělo být použitelné v rámci široké škály případů použití, aniž by došlo k narušení výkonu.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-115">**General purpose and performant** – the framework should be usable by as broad a range of use-cases as possible without compromising performance.</span></span>
- <span data-ttu-id="f8ca6-116">**Streaming** – protokol by měl poskytovat sémantiku streamování pro velké datové sady nebo asynchronní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-116">**Streaming** – the protocol should provide streaming semantics for large data-sets or asynchronous messaging.</span></span>
- <span data-ttu-id="f8ca6-117">**Výměna metadat** – protokol povoluje zpracování neobchodních dat, jako jsou tokeny ověřování, odděleně od skutečných obchodních dat.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-117">**Metadata exchange** – the protocol allow non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="f8ca6-118">**Standardizované stavové kódy** – proměnlivost chybových kódů by měla být snížena, aby se zajistilo, že se postará rozhodnutí o zpracování chyb a v případě nutnosti dalšího podrobnějšího zpracování chyb by měl být k dispozici mechanismus pro správu v rámci výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-118">**Standardized status codes** – the variability of error codes should be reduced to make error handling decisions clearer and, where additional richer error handling is required, a mechanism should be provided for managing this within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f8ca6-119">[Předchozí](introduction.md)
>[Další](approach.md)</span><span class="sxs-lookup"><span data-stu-id="f8ca6-119">[Previous](introduction.md)
[Next](approach.md)</span></span>
