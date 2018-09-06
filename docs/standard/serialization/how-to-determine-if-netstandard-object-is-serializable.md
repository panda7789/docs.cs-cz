---
title: Jak zjistit, zda je objekt .NET Standard serializovat
description: Ukazuje, jak určit, zda lze typu .NET Standard serializovat v době běhu.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881405"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Jak zjistit, zda je objekt .NET Standard serializovat

.NET Standard je specifikace, která definuje typy a členy, které musí být k dispozici na konkrétní implementace rozhraní .NET, které odpovídají verzi standard. Ale .NET Standard není definován, zda je typ serializovat. Typy definované ve standardní knihovně .NET nejsou označené <xref:System.SerializableAttribute> atribut. Místo toho jsou konkrétní implementace .NET, jako je například rozhraní .NET Framework a .NET Core, rozhodnout, zda je určitý typ serializovat. 

Pokud jste vytvořili knihovnu, který cílí na .NET Standard, knihovny mohou využívat všechny implementace .NET, který podporuje .NET Standard. To znamená, že nelze víte předem, zda je určitý typ serializovatelný; pouze můžete určit, zda je serializovatelný v době běhu.

Můžete určit, zda je objekt za běhu serializovatelný načtením hodnoty <xref:System.Type.IsSerializable> vlastnost <xref:System.Type> objekt, který představuje typ tohoto objektu. V následujícím příkladu poskytuje jedna implementace. Definuje `IsSerializable(Object)` rozšiřující metoda, která označuje, zda se mají <xref:System.Object> lze serializovat instance.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Libovolný objekt můžete předat metodě k určení, zda ho může serializaci a deserializaci na aktuální implementace .NET, jako v následujícím příkladu:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Viz také:

- [Binární serializace](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
