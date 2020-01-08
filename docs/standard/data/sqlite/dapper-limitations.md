---
title: Omezení dapperem
ms.date: 12/13/2019
description: Popisuje některá omezení, která se objeví při použití Dapperem.
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447277"
---
# <a name="dapper-limitations"></a><span data-ttu-id="6b88c-103">Omezení dapperem</span><span class="sxs-lookup"><span data-stu-id="6b88c-103">Dapper limitations</span></span>

<span data-ttu-id="6b88c-104">Při použití Microsoft. data. sqlite s [dapperem](https://stackexchange.github.io/Dapper/)je třeba vzít v úvahu několik omezení.</span><span class="sxs-lookup"><span data-stu-id="6b88c-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="6b88c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b88c-105">Parameters</span></span>

<span data-ttu-id="6b88c-106">Názvy parametrů SQLite rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="6b88c-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="6b88c-107">Zajistěte, aby názvy parametrů používané v SQL odpovídaly velikostem vlastností anonymního objektu.</span><span class="sxs-lookup"><span data-stu-id="6b88c-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="6b88c-108">Problém [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) by vylepšil toto prostředí.</span><span class="sxs-lookup"><span data-stu-id="6b88c-108">Issue [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="6b88c-109">Dapperem také očekává parametry pro použití předpony `@`.</span><span class="sxs-lookup"><span data-stu-id="6b88c-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="6b88c-110">Jiné předpony nebudou fungovat.</span><span class="sxs-lookup"><span data-stu-id="6b88c-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="6b88c-111">Typy dat</span><span class="sxs-lookup"><span data-stu-id="6b88c-111">Data types</span></span>

<span data-ttu-id="6b88c-112">Dapperem čte hodnoty pomocí indexeru SqliteDataReader.</span><span class="sxs-lookup"><span data-stu-id="6b88c-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="6b88c-113">Návratový typ tohoto indexeru je objekt, což znamená, že bude vracet pouze hodnoty Long, Double, String nebo Byte [].</span><span class="sxs-lookup"><span data-stu-id="6b88c-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="6b88c-114">Další informace najdete v tématu [datové typy](types.md).</span><span class="sxs-lookup"><span data-stu-id="6b88c-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="6b88c-115">Dapperem zpracovává většinu převodů mezi těmito a dalšími primitivními typy.</span><span class="sxs-lookup"><span data-stu-id="6b88c-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="6b88c-116">Bohužel nezpracovává `DateTimeOffset`, `Guid`nebo `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="6b88c-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="6b88c-117">Vytvořte obslužné rutiny typů, pokud chcete použít tyto typy ve výsledcích.</span><span class="sxs-lookup"><span data-stu-id="6b88c-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="6b88c-118">Nezapomeňte před dotazování přidat obslužné rutiny typů.</span><span class="sxs-lookup"><span data-stu-id="6b88c-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="6b88c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b88c-119">See also</span></span>

* [<span data-ttu-id="6b88c-120">Datové typy</span><span class="sxs-lookup"><span data-stu-id="6b88c-120">Data types</span></span>](types.md)
* [<span data-ttu-id="6b88c-121">Asynchronní omezení</span><span class="sxs-lookup"><span data-stu-id="6b88c-121">Async limitations</span></span>](async.md)
