---
title: -Nullable (možnosti kompilátoru C#)
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449811"
---
# <a name="-nullable-c-compiler-options"></a>-Nullable (možnosti kompilátoru C#)

Možnost **-Nullable** umožňuje zadat požadovaný kontext s možnou hodnotou null.

## <a name="syntax"></a>Syntaxe

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`  
Zadáním `+` nebo pouhou **možnou hodnotou null**způsobí, že kompilátor povolí kontext s možnou hodnotou null. Určení `-` , které platí v případě, že neurčíte **hodnotu**null, zakážete kontext s možnou hodnotou null.

`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`  
Určuje možnost kontextu s možnou hodnotou null. Podobně jako `+` nebo `-` , pokud chcete povolit a zakázat, ale umožňuje více členitosti kontextu s možnou hodnotou null. `enable`Argument, který je platný, jako Pokud zadáte **hodnotu null**, povoluje kontext s možnou hodnotou null. Při zadání `disable` se zakáže kontext s možnou hodnotou null. Při zadání `warnings` argumentu **-Nullable:** Warnings je povolený kontext s možnou hodnotou null. Při zadávání `annotations` argumentu **-Nullable: Annotations**je povolený kontext anotace s možnou hodnotou null.

## <a name="remarks"></a>Poznámky

Analýza toku se používá k odvození hodnoty null proměnných v rámci spustitelného kódu. Odvozená hodnota null proměnné je nezávislá na deklarované hodnotě null proměnné. Volání metod jsou analyzována i v případě, že jsou podmíněně vynechána. Například <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> v režimu vydání.

Vyvolání metod popsaných s následujícími atributy ovlivní také analýzu toků:

- Jednoduché předběžné podmínky: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> a<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Jednoduché následné stavy: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> a<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Podmíněné následné podmínky: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> a<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>(např. `DoesNotReturnIf(false)` pro <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) a<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Stavy po členu: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> a<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

### <a name="to-set-this-compiler-option-in-a-project"></a>Nastavení této možnosti kompilátoru v projektu

Úpravou *. csproj* přidejte `<Nullable>` značku v `Project/PropertyGroup` hierarchii:

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
