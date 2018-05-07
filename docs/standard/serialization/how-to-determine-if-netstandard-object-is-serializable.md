---
title: 'Postupy: určit, zda je serializovatelný objekt .NET Standard'
description: Ukazuje, jak určit, zda lze serializovat typu .NET Standard v době běhu.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 247eed2e7091930c6bcfaa524296b45350dd6510
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Postupy: určit, zda je serializovatelný objekt .NET Standard

.NET Standard je specifikace, která určuje typy a členy, které musí být na konkrétní implementace rozhraní .NET, které odpovídat příslušné verzi nástroje standard. Ale .NET Standard nedefinuje zda je typu serializable. Typy definované v standardní knihovny .NET nejsou označené jako <xref:System.SerializableAttribute> atribut. Konkrétní implementace rozhraní .NET, například rozhraní .NET Framework a .NET Core, místo toho mohou rozhodnout, zda je konkrétní typ serializovatelný. 

Když jste vyvinutý knihovny s cílem .NET Standard, vaše knihovna mohou být spotřebovávána žádné implementace rozhraní .NET, která podporuje .NET Standard. To znamená, že nelze znát předem zda je konkrétní typ serializovatelný; pouze můžete zjistit, zda je serializovatelný za běhu.

Můžete určit, zda je objekt serializovatelný za běhu načtením hodnotu <xref:System.Type.IsSerializable> vlastnost <xref:System.Type> objekt, který představuje typ tohoto objektu. Následující příklad poskytuje jednu implementaci. Definuje, `IsSerializable(Object)` metoda rozšíření, která určuje, zda se mají <xref:System.Object> instance lze serializovat.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Jakýkoli objekt můžete poté předat metodě k určení, zda lze serializovat a deserializovat na aktuální implementace rozhraní .NET, jak ukazuje následující příklad:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a>Viz také

[Binární serializace](binary-serialization.md)   
<xref:System.SerializableAttribute?displayProperty=nameWithType>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
