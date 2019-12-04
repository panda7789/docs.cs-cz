---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711665"
---
# <a name="reflection-c"></a>Reflexe (C#)

Reflexe poskytuje objekty (typu <xref:System.Type>), které popisují sestavení, moduly a typy. Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získat typ z existujícího objektu a vyvolat jeho metody nebo získat přístup k jeho polím a vlastnostem. Pokud používáte atributy v kódu, reflexe vám umožní přístup k nim. Další informace najdete v tématu [atributy](../../../standard/attributes/index.md).

Tady je jednoduchý příklad reflexe pomocí metody <xref:System.Object.GetType> – zděděné všemi typy ze `Object` základní třídy – pro získání typu proměnné:

> [!NOTE]
> Ujistěte se, že jste přidali `using System;` a `using System.Reflection;` v horní části souboru *. cs* .

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Výstup je: `System.Int32`.

Následující příklad používá reflexi k získání úplného názvu načteného sestavení.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Výstup je: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> C# Klíčová slova `protected` a `internal` nemají význam v Il a nejsou použity v rozhraních API reflexe. Odpovídající výrazy v IL jsou *rodina* a *sestavení*. Chcete-li identifikovat metodu `internal` pomocí reflexe, použijte vlastnost <xref:System.Reflection.MethodBase.IsAssembly%2A>. K identifikaci `protected internal` metody použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Přehled reflexe

Reflexe je užitečná v následujících situacích:

- Pokud budete mít přístup k atributům v metadatech vašeho programu. Další informace najdete v tématu [načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Pro zkoumání a vytváření instancí typů v sestavení.
- Pro vytváření nových typů za běhu. Použijte třídy v <xref:System.Reflection.Emit>.
- Pro provádění pozdní vazby získáte přístup k metodám typů vytvořeným v době běhu. Viz téma [Dynamické načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).

## <a name="related-sections"></a>Související oddíly

Další informace:

- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)
- [Zobrazení informací o typu](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
