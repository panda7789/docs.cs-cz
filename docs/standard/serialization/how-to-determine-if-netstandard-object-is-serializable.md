---
title: Jak zjistit, zda je objekt .NET Standard serializovatelný
description: Ukazuje, jak určit, zda lze typ .NET Standard serializovat v době běhu.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: b6791ae0666aeb0ac02d8a38ca419d7de2b263cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289600"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Jak zjistit, zda je objekt .NET Standard serializovatelný

.NET Standard je specifikace definující typy a členy, které musí být přítomny v konkrétních implementacích .NET, které odpovídají této verzi standardu. .NET Standard však nedefinuje, zda je typ serializovatelný. Typy definované v knihovně .NET Standard nejsou označeny <xref:System.SerializableAttribute> atributem. Místo toho je možné určit, zda je konkrétní typ serializovatelný, konkrétní implementaci rozhraní .NET, například .NET Framework a .NET Core.

Pokud jste vytvořili knihovnu, která cílí na .NET Standard, vaše knihovna může být spotřebována jakoukoli implementací .NET, která podporuje .NET Standard. To znamená, že nemůžete předem znát, zda je konkrétní typ serializovatelný; můžete určit, zda je v době běhu serializovatelný.

Můžete určit, zda je objekt serializovatelný za běhu načtením hodnoty <xref:System.Type.IsSerializable> vlastnosti <xref:System.Type> objektu, který představuje typ daného objektu. Následující příklad poskytuje jednu implementaci. Definuje `IsSerializable(Object)` metodu rozšíření, která označuje, zda <xref:System.Object> může být jakákoli instance serializována.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Pak můžete předat libovolný objekt metodě, abyste zjistili, zda lze serializovat a deserializovat v aktuální implementaci rozhraní .NET, jak ukazuje následující příklad:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Viz také

- [Binární serializace](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
