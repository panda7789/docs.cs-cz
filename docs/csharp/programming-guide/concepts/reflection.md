---
title: Reflexe (C#)
ms.date: 07/20/2015
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
ms.openlocfilehash: a56fb24b63e4d80dbb67b079466b67cd11672023
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711665"
---
# <a name="reflection-c"></a>Reflexe (C#)

Reflexe poskytuje objekty (typu), <xref:System.Type>které popisují sestavení, moduly a typy. Reflexe můžete použít k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získání typu z existujícího objektu a vyvolání jeho metod nebo přístupu k jeho polím a vlastnostem. Pokud používáte atributy v kódu, reflexe umožňuje přístup k nim. Další informace naleznete v [tématu Atributy](../../../standard/attributes/index.md).

Zde je jednoduchý příklad reflexe <xref:System.Object.GetType> pomocí metody - zděděné všemi typy ze `Object` základní třídy - chcete-li získat typ proměnné:

> [!NOTE]
> Ujistěte se, že přidáte `using System;` a `using System.Reflection;` v horní části souboru *.cs.*

```csharp
// Using GetType to obtain type information:
int i = 42;
Type type = i.GetType();
Console.WriteLine(type);
```

Výstup je: `System.Int32`.

Následující příklad používá reflexe k získání úplného názvu načteného sestavení.

```csharp
// Using Reflection to get information of an Assembly:
Assembly info = typeof(int).Assembly;
Console.WriteLine(info);
```

Výstup je: `System.Private.CoreLib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=7cec85d7bea7798e`.

> [!NOTE]
> C# klíčová `protected` slova `internal` a nemají žádný význam v IL a nejsou použity v reflexi API. Odpovídající termíny v IL jsou *rodina* a *sestavení*. Chcete-li `internal` identifikovat metodu <xref:System.Reflection.MethodBase.IsAssembly%2A> pomocí reflexe, použijte vlastnost. Chcete-li `protected internal` identifikovat metodu, použijte <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.

## <a name="reflection-overview"></a>Přehled reflexe

Reflexe je užitečná v následujících situacích:

- Pokud máte přístup k atributům v metadatech programu. Další informace naleznete v [tématu Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md).
- Pro zkoumání a vytváření konkretistů typů v sestavení.
- Pro vytváření nových typů za běhu. Použití tříd <xref:System.Reflection.Emit>v .
- Pro provádění pozdní vazby, přístup k metodám na typy vytvořené v době běhu. Podívejte se na téma [Dynamicky načítání a používání typů](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).

## <a name="related-sections"></a>Související oddíly

Další informace najdete tady:

- [Reflexe](../../../framework/reflection-and-codedom/reflection.md)
- [Zobrazení informací o typu](../../../framework/reflection-and-codedom/viewing-type-information.md)
- [Reflexe a obecné typy](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)
- <xref:System.Reflection.Emit>
- [Načítání informací uložených v atributech](../../../standard/attributes/retrieving-information-stored-in-attributes.md)

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
