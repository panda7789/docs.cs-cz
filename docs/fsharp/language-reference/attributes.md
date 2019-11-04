---
title: Atributy
description: Zjistěte, F# jak atributy umožňují použít metadata pro programovací konstrukci.
ms.date: 05/16/2016
ms.openlocfilehash: 223263f5789b0fc7eb2b3ef2905f6436980bd14a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424802"
---
# <a name="attributes"></a>Atributy

Atributy umožňují použít metadata pro programovací konstrukci.

## <a name="syntax"></a>Syntaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi je *cíl* nepovinný a, pokud je k dispozici, určuje druh entity programu, na kterou se atribut vztahuje. V tabulce, která se objeví později v tomto dokumentu, se zobrazí platné hodnoty pro *cíl* .

*Název atributu* odkazuje na název (případně kvalifikovaný pro obory názvů) platného typu atributu s příponou nebo bez přípony `Attribute`, která se obvykle používá v názvech typů atributů. Například typ `ObsoleteAttribute` může být zkrácen na pouze `Obsolete` v tomto kontextu.

*Argumenty* jsou argumenty konstruktoru pro typ atributu. Pokud má atribut konstruktor bez parametrů, lze seznam argumentů a kulaté závorky vynechat. Atributy podporují Poziční argumenty i pojmenované argumenty. *Poziční argumenty* jsou argumenty, které jsou používány v pořadí, ve kterém jsou uvedeny. Pojmenované argumenty lze použít, pokud má atribut veřejné vlastnosti. Můžete je nastavit pomocí následující syntaxe v seznamu argumentů.

```fsharp
property-name = property-value
```

Tyto inicializace vlastností mohou být v libovolném pořadí, ale musí následovat za libovolnými pozičními argumenty. Následuje příklad atributu, který používá poziční argumenty a inicializace vlastností:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

V tomto příkladu je atribut `DllImportAttribute`, který se používá v zkráceném formátu. První argument je poziční parametr a druhý je vlastnost.

Atributy jsou programovací konstrukce .NET, která umožňuje objekt známý jako *atribut* , který má být přidružen k typu nebo jinému prvku programu. Prvek program, pro který je atribut použit, je označován jako *cíl atributu*. Atribut obvykle obsahuje metadata o jeho cíli. V tomto kontextu metadata mohou být jakákoli data o jiném typu než jeho pole a členové.

Atributy v F# lze použít u následujících programovacích konstrukcí: funkce, metody, sestavení, moduly, typy (třídy, záznamy, struktury, rozhraní, delegáti, výčty, sjednocení atd.), konstruktory, vlastnosti, pole, parametry, parametry typu a návratové hodnoty. Atributy nejsou povoleny u vazeb `let` v rámci tříd, výrazů nebo výrazů pracovního postupu.

Obvykle se deklarace atributu zobrazuje přímo před deklarací cíle atributu. Deklarace více atributů lze použít společně následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Můžete zadat dotaz na atributy za běhu pomocí reflexe rozhraní .NET.

Můžete deklarovat více atributů jednotlivě, jako v předchozím příkladu kódu, nebo je můžete deklarovat v jedné sadě hranatých závorek, pokud použijete středník pro oddělení jednotlivých atributů a konstruktorů, a to následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Obvykle zjištěné atributy zahrnují atribut `Obsolete`, atributy pro požadavky na zabezpečení, atributy pro podporu modelu COM, atributy, které se vztahují k vlastnictví kódu a atributy, které označují, zda lze typ serializovat. Následující příklad ukazuje použití atributu `Obsolete`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Pro cíle atributů `assembly` a `module`použijete atributy na `do` vazbu na nejvyšší úrovni v sestavení. Do deklarace atributu můžete zahrnout slovo `assembly` nebo `module` následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Pokud vynecháte cíl atributu pro atribut, který je použit pro `do` vazby, F# kompilátor se pokusí určit cíl atributu, který dává smysl pro tento atribut. Mnoho tříd atributů má atribut typu `System.AttributeUsageAttribute`, který obsahuje informace o možných cílech podporovaných pro tento atribut. Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje funkce jako cíle, atribut je pořízen pro použití pro hlavní vstupní bod programu. Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje sestavení jako cíle, kompilátor vezme atribut, který má být použit pro sestavení. Většina atributů se nevztahuje na funkce i sestavení, ale v případech, kdy jsou, se atribut povede pro použití v hlavní funkci programu. Pokud je cíl atributu explicitně zadán, je atribut použit pro zadaný cíl.

Přestože nemusíte obvykle explicitně určovat cíl atributu, platné hodnoty pro *cíl* v atributu spolu s příklady použití jsou uvedeny v následující tabulce:

<table>
  <tr>
    <th>Cíl atributu</td>
    <th>Příklad</td>
  </tr>
  <tr>
    <td>sestavení</td>
    <td><pre lang="fsharp"><code>[&lt;assembly: AssemblyVersionAttribute("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>return</td>
    <td><pre lang="fsharp"><code>let function1 x : [&lt;return: Obsolete&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td>pole</td>
    <td><pre lang="fsharp"><code>[&lt;field: DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td>property</td>
    <td><pre lang="fsharp"><code>[&lt;property: Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td>Bajty</td>
    <td><pre lang="fsharp"><code>member this.MyMethod([&lt;param: Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td>– typ</td>
    <td>
        <pre lang="fsharp"><code>
[&lt;type: StructLayout(Sequential)&gt;]
type MyStruct =
struct
x : byte
y : int
end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
