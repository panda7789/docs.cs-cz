---
title: Atributy (F#)
description: 'Zjistěte, jak povolit F # atributy metadata, která má být použita pro programovací konstrukce.'
ms.date: 05/16/2016
ms.openlocfilehash: 107f5d9cbcce28c97fc5b738759ef27649fc45a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565422"
---
# <a name="attributes"></a>Atributy

Atributy povolit metadata, která má být použita pro programovací konstrukce.

## <a name="syntax"></a>Syntaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Poznámky

V předchozích syntaxe *cíl* je volitelný a pokud je k dispozici, určuje druh program entita, která se vztahuje na atribut. Platné hodnoty pro *cíl* jsou uvedené v tabulce, která se zobrazí později v tomto dokumentu.

*Název atributu* odkazuje na název (může být kvalifikovaný pomocí oborů názvů) typu atributu platný, s nebo bez přípona `Attribute` , obvykle se používá v názvech typ atributu. Například typ `ObsoleteAttribute` lze zkrátit těsně `Obsolete` v tomto kontextu.

*Argumenty* jsou argumenty pro konstruktor pro typ atributu. Pokud atribut má výchozí konstruktor, můžete vynechat seznam argumentů a závorek. Atributy podporovat poziční argumenty a pojmenované argumenty. *Poziční argumenty* argumenty, které se používají v pořadí, ve kterém jsou zobrazeny. Pojmenované argumenty lze použít, pokud má atribut veřejné vlastnosti. Můžete nastavit tak, že pomocí následující syntaxe v seznamu argumentů.

```
*property-name* = *property-value*
```

Taková vlastnost inicializacích může být v libovolném pořadí, ale se musí řídit všechny poziční argumenty. Následuje příklad atribut, který používá poziční argumentů a inicializacích vlastnost.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

V tomto příkladu je atribut `DllImportAttribute`, zde použít ve zkráceném tvaru. První argument je parametr poziční a druhý je vlastnost.

Atributy jsou .NET programovací konstrukce, která umožňuje objekt známé jako *atribut* přidruženou typu nebo jiného programu elementu. Element program, do které se použije atribut se označuje jako *atribut target*. Atribut obvykle obsahuje metadata o cíli. V tomto kontextu může být metadata žádná data o typu než jeho polí a členy.

Atributy v jazyce F # lze použít pro následující programovací konstrukce: funkce, metody, sestavení, moduly, typy (třídy, záznamy, struktury, rozhraní, delegáti, výčty, sjednocení a tak dále), konstruktory, vlastnosti, pole, parametry, Zadejte parametry a návratové hodnoty. Atributy nejsou povoleny na `let` vazby uvnitř tříd, výrazy a výrazy pracovního postupu.

Deklaraci atributu se obvykle zobrazuje přímo před deklaraci atribut target. Více deklarací atribut je možné společně, a to takto.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

V době běhu pomocí reflexe .NET můžete dotazovat atributy.

Je možné deklarovat několik atributů jednotlivě, jako v předchozím příkladu kódu, nebo je možné deklarovat v jedné sadě závorky a pokud používáte středníkem oddělte jednotlivé atributy a konstruktory, jak je vidět tady.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Obvykle došlo k atributy patří `Obsolete` atribut atributy pro aspekty zabezpečení, atributy pro podporu modelu COM, atributy, které se týkají vlastnictví kódu a atributy, která určuje, zda lze serializovat typu. Následující příklad ukazuje použití `Obsolete` atribut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Pro atribut cíle `assembly` a `module`, použijete atributy nejvyšší úrovně `do` vazby ve vašem sestavení. Můžete použít slovo `assembly` nebo `module` v deklaraci atributu, následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Pokud je cílem atributu pro atribut u vynechat `do` vazby, kompilátor jazyka F # se pokusí určit atribut target, která je vhodná pro tento atribut. Mnoho atribut třídy mají atribut typu `System.AttributeUsageAttribute` , který obsahuje informace o možných cíle pro tento atribut podporována. Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje funkce jako cíle atribut se provede chcete použít pro hlavní vstupní bod programu. Pokud `System.AttributeUsageAttribute` označuje, že atribut podporuje sestavení jako cíle kompilátor trvá atribut, který chcete použít pro sestavení. Většina atributy se nevztahují na funkce a sestavení, ale v případech, kde udělají, je atribut prováděné chcete použít pro hlavní funkce programu. Pokud cílový atribut je explicitně zadána, atribut se používá k zadané cílové.

I když není nutné obvykle zadat atribut cíle explicitně, platné hodnoty pro *cíl* v atributu, které jsou uvedeny v následující tabulce, společně s příklady využití.

<table>
  <tr>
    <th>Atribut target</td>
    <th>Příklad</td> 
  </tr>
  <tr>
    <td>sestavení</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>' umožní function1 x: [<return: Obsolete>] int = x + 1</td> 
  </tr>
  <tr>
    <td>pole</td>
    <td>"[<field: DefaultValue>] val měnitelný x: int.</td> 
  </tr>
  <tr>
    <td>property</td>
    <td>"[<property: Obsolete>] to. MyProperty = x.</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>člen to. MyMethod ([<param: Out>] x: ref<int>) = x: = 10</td> 
  </tr>
  <tr>
    <td>– typ</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>] zadejte MyStruct = struktura x: y bajtů: int end ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka F#](index.md)
