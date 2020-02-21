---
title: Přehled gRPC-gRPC pro vývojáře WCF
description: Seznamte se se sadou principů, které vyvíjejí vývoj gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: a0811adadc617097d86edc5f845c42a7e90f560f
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542920"
---
# <a name="grpc-overview"></a><span data-ttu-id="1e452-103">gRPC – přehled</span><span class="sxs-lookup"><span data-stu-id="1e452-103">gRPC overview</span></span>

<span data-ttu-id="1e452-104">Po prohlédnutí Genesis Windows Communication Foundation (WCF) a gRPC v poslední části Tato kapitola zohledňuje některé klíčové funkce gRPC a jejich porovnání s WCF.</span><span class="sxs-lookup"><span data-stu-id="1e452-104">After looking at the genesis of both Windows Communication Foundation (WCF) and gRPC in the last chapter, this chapter considers some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="1e452-105">ASP.NET Core 3,0 je první verze ASP.NET, která nativně podporuje gRPC jako občana první třídy, s týmy Microsoftu, které přispívají k oficiální implementaci rozhraní .NET gRPC.</span><span class="sxs-lookup"><span data-stu-id="1e452-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="1e452-106">Doporučuje se pro vytváření distribuovaných aplikací s .NET, které mohou spolupracovat se všemi ostatními hlavními programovacími jazyky a architekturami.</span><span class="sxs-lookup"><span data-stu-id="1e452-106">It's recommended for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="1e452-107">Hlavní principy</span><span class="sxs-lookup"><span data-stu-id="1e452-107">Key principles</span></span>

<span data-ttu-id="1e452-108">Jak je popsáno v kapitole 1, Google chtěla použít zavedení HTTP/2 k nahrazení Stubby, jeho interní infrastruktury RPC pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="1e452-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to replace Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="1e452-109">gRPC založené na Stubby teď můžou využít standardizaci a by rozšířily její použitelnost na Mobile Computing, Cloud a Internet věcí.</span><span class="sxs-lookup"><span data-stu-id="1e452-109">gRPC, based on Stubby, now can take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="1e452-110">Za tímto účelem vytvořila sada [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) sadu principů, které by se řídily gRPC.</span><span class="sxs-lookup"><span data-stu-id="1e452-110">To achieve this, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="1e452-111">V následujícím seznamu jsou uvedeny nejdůležitější ty, které se hlavně týkají maximalizace usnadnění přístupu a použitelnosti:</span><span class="sxs-lookup"><span data-stu-id="1e452-111">The following list shows the most relevant ones, which are mainly concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="1e452-112">**Free a Open** – všechny artefakty by měly být open source s licencováním, které nebrání vývojářům v přijímání gRPC.</span><span class="sxs-lookup"><span data-stu-id="1e452-112">**Free and open** – All artifacts should be open source, with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="1e452-113">**Pokrytí a jednoduchost** – gRPC by měly být k dispozici napříč všemi oblíbenými platformami a dostatečně snadné pro sestavování na jakékoli platformě.</span><span class="sxs-lookup"><span data-stu-id="1e452-113">**Coverage and simplicity** – gRPC should be available across every popular platform, and simple enough to build on any platform.</span></span>
- <span data-ttu-id="1e452-114">**Interoperabilita a dosah** – je vhodné používat gRPC v jakékoli síti bez ohledu na šířku pásma nebo latenci pomocí široce dostupných síťových standardů.</span><span class="sxs-lookup"><span data-stu-id="1e452-114">**Interoperability and reach** – It should be possible to use gRPC on any network, regardless of bandwidth or latency, by using widely available network standards.</span></span>
- <span data-ttu-id="1e452-115">**Obecný účel a** výkon – rozhraní by mělo být použitelné v rámci široké škály případů použití, aniž by to ohrozilo výkon.</span><span class="sxs-lookup"><span data-stu-id="1e452-115">**General purpose and performant** – The framework should be usable by as broad a range of use-cases as possible, without compromising performance.</span></span>
- <span data-ttu-id="1e452-116">**Streaming** – protokol by měl poskytovat sémantiku streamování pro velké datové sady nebo asynchronní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="1e452-116">**Streaming** – The protocol should provide streaming semantics for large datasets or asynchronous messaging.</span></span>
- <span data-ttu-id="1e452-117">**Výměna metadat** – protokol umožňuje zpracovávat neobchodní data, jako jsou tokeny ověřování, odděleně od skutečných obchodních dat.</span><span class="sxs-lookup"><span data-stu-id="1e452-117">**Metadata exchange** – The protocol allows non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="1e452-118">**Standardizované stavové kódy** – proměnlivost chybových kódů by měla být snížena, aby se zajistilo, že se postará rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="1e452-118">**Standardized status codes** – The variability of error codes should be reduced to make error handling decisions clearer.</span></span> <span data-ttu-id="1e452-119">V případě, že je potřeba další, rozsáhlejší zpracování chyb, by měl být k dispozici mechanismus pro správu tohoto serveru v rámci výměny metadat.</span><span class="sxs-lookup"><span data-stu-id="1e452-119">Where additional, richer error handling is required, a mechanism should be provided for managing this within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1e452-120">[Předchozí](introduction.md)
>[Další](approach.md)</span><span class="sxs-lookup"><span data-stu-id="1e452-120">[Previous](introduction.md)
[Next](approach.md)</span></span>
