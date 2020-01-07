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
# <a name="dapper-limitations"></a>Omezení dapperem

Při použití Microsoft. data. sqlite s [dapperem](https://stackexchange.github.io/Dapper/)je třeba vzít v úvahu několik omezení.

## <a name="parameters"></a>Parametry

Názvy parametrů SQLite rozlišují velká a malá písmena. Zajistěte, aby názvy parametrů používané v SQL odpovídaly velikostem vlastností anonymního objektu. Problém [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) by vylepšil toto prostředí.

Dapperem také očekává parametry pro použití předpony `@`. Jiné předpony nebudou fungovat.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a>Typy dat

Dapperem čte hodnoty pomocí indexeru SqliteDataReader. Návratový typ tohoto indexeru je objekt, což znamená, že bude vracet pouze hodnoty Long, Double, String nebo Byte []. Další informace najdete v tématu [datové typy](types.md). Dapperem zpracovává většinu převodů mezi těmito a dalšími primitivními typy. Bohužel nezpracovává `DateTimeOffset`, `Guid`nebo `TimeSpan`. Vytvořte obslužné rutiny typů, pokud chcete použít tyto typy ve výsledcích.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

Nezapomeňte před dotazování přidat obslužné rutiny typů.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a>Viz také:

* [Datové typy](types.md)
* [Asynchronní omezení](async.md)
