---
description: -Nullable (možnosti kompilátoru C#)
title: -Nullable (možnosti kompilátoru C#)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125043"
---
# <a name="-nullable-c-compiler-options"></a>-Nullable (možnosti kompilátoru C#)

Možnost **-Nullable** umožňuje zadat požadovaný kontext s možnou hodnotou null.

## <a name="syntax"></a>Syntaxe

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Argumenty

`+` &#124; `-`  
Zadáním `+` nebo pouhou **možnou hodnotou null**způsobí, že kompilátor povolí kontext s možnou hodnotou null. Určení `-` , které platí v případě, že neurčíte **hodnotu**null, zakážete kontext s možnou hodnotou null.

`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`  
Určuje možnost kontextu s možnou hodnotou null. Podobně jako `+` nebo `-` , pokud chcete povolit a zakázat, ale umožňuje více členitosti kontextu s možnou hodnotou null. `enable`Argument, který je platný, jako Pokud zadáte **hodnotu null**, povoluje kontext s možnou hodnotou null. Při zadání `disable` se zakáže kontext s možnou hodnotou null. Při zadání `warnings` argumentu **-Nullable:** Warnings je povolený kontext s možnou hodnotou null. Při zadávání `annotations` argumentu **-Nullable: Annotations**je povolený kontext anotace s možnou hodnotou null.

## <a name="remarks"></a>Poznámky

Analýza toku se používá k odvození hodnoty null proměnných v rámci spustitelného kódu. Odvozená hodnota null proměnné je nezávislá na deklarované hodnotě null proměnné. Volání metod jsou analyzována i v případě, že jsou podmíněně vynechána. Například <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> v režimu vydání.

Vyvolání metod popsaných s následujícími atributy ovlivní také analýzu toků:

- Jednoduché předběžné podmínky: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> a <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Jednoduché následné stavy: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> a <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Podmíněné následné podmínky: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> a <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (například `DoesNotReturnIf(false)` pro <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) a <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Stavy po členu: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> a <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>Nastavení této možnosti kompilátoru v projektu

Upravte soubor *. csproj* pro přidání `<Nullable>` značky v rámci `Project/PropertyGroup` hierarchie:

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Odkazové typy s možnou hodnotou null](../../nullable-references.md)
